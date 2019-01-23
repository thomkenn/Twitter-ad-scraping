# Twitter-ad-scaping
Uses Phantom.JS and node.js to create a pipeline for twitter ad data on election candidates. 

The twitter API for ad information on political candidates is sadly lacking in functionality. It doesnt have an API and it doesnt tell you historic data for a candidate. Using this tool, you can take daily snapshots of political candidates and store their total campaign spening in a database for later use. With daily snapshots of total spend, you can see how much they are spending every day on political campaigns. 

Instructions for use in a ec2 or other linux based instance: 

Create a table in a MYSQL database for each candidate you want to track with a date and an amount. Be sure to use a short descriptive name for the table.

```
create table Gillibrand (date varchar(5), amount float(10));
create table Kamala (date varchar(5), amount float(10));
create table Beto (date varchar(5), amount float(10));
create table Bernie (date varchar(5), amount float(10));
create table Warren (date varchar(5), amount float(10));
create table Klobuchar (date varchar(5), amount float(10));
```
Install phantomjs, node.js, and screen.

Plug in your credentials for your MYSQL db into auth.json

Type in:

```
touch output.csv

screen

phantomjs poli.js
```
Then hit ctrl + a + d to escape the screen without closing it. Then type:

```
node main.js
```

And you're done. The main.js will check the output.csv for any changes and update your db as soon as a change occurs. After reading, main.js will wipe the output.csv and go back into sleep mode, waiting for changes.

This project is still firmly in alpha, and contains several critical bugs that are more likely to occur the longer it has been running, and is dependent on phantom.js, a project that is no longer active and is not recieving updates. Use at your own risk. 


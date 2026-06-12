---
title: "Snort not opening, error on DB abstraction library $DBlib_path in base_conf.php"
date: 2014-11-07
forum: General Help
---

### Post by Kimona on 2014-11-07
Hello Ubuntu gurus...

I am seeking some help with a problem with Snort not opening the BASE website. I am running Ubuntu 14.04 in a virtual environment. I have followed the Snort installation instructions to the T I have edit the _conf.php file using [SIZE=3][FONT=CMTT8][FONT=CMTT8]
sudo nano / var / www / html / base / base \ _conf .php
[/FONT][/FONT][/SIZE][FONT=CMTT8][SIZE=1][FONT=CMTT8][SIZE=1] 
[/SIZE][/FONT][/SIZE][/FONT]
made the changes bellow: 

[FONT=CMTT10][SIZE=2][FONT=CMTT10][SIZE=2]$BASE_urlpath = '/base';         # line 50
$DBlib_path = '/var/adodb/';    # line 80
$alert_dbname = 'snort';           # line 102
$alert_host = 'localhost';
$alert_port = '';
$alert_user = 'snort';
$alert_password = 'PASSWORD'; # line 106
[/SIZE][/FONT][/SIZE][/FONT]
but I am not sure why it does not load the website. Any ideas why or how can I fix this problem?

 Any help would be appreciated, Thanks!

This is the Error the website displays:

**Error loading the DB Abstraction library: ** from "/var/www/html/adodb/adodb.inc.php"

Check the DB abstraction library variable $DBlib_path in base_conf.php
            
The underlying database library currently used is ADODB, that can be downloaded at [http://adodb.sourceforge.net/](http://adodb.sourceforge.net/)

snort-2.9.7.0, ubunt 14.04, base system error, adodb,

---


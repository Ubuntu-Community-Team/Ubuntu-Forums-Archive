---
title: "Can't create database"
date: 2007-11-14
forum: General Help
---

### Post by Necromantis on 2007-11-14
I'm stuck on this one..

I have installed Ubuntu Server 7.x, made some VirtualHosts configure Samba, and that part works fine (actually it works MUCH faster than the WAMP). So I got to the point where I need to transfer my data from MySQL on XP to MySQL on Ubuntu.

1st idea was to copy paste 1 of the folder from the wamp/mysql/data into /var/lib/mysql .. obviously that didn't work so I deleted the folder.

2nd idea was to use phpmyadmin to backup the file on XP and Import it back on Ubuntu. Backup worked fine but then I realised I didn't have phpmyadmin on Ubuntu so I did a swift:

sudo apt-get install phpmyadmin

which got it sorted. 

I logon from my XP machine to 127.0.0.1/phpmyadmin as root with pass and realised I didn't reall have access because out of the localhost so I went on the server an manually created a new user , let's call him john , with all privileges grant on %

I went back on my PC and login to phpmyadmin with john and tried something fairly simple: create a new database, lets call it: fire . phpmyadmin then returned an error message: Can't create database 'fire' (errno: 13)  :confused:

At which point I start to not understand.. john as full access on all IPs so it should have worked.. so perhaps there is something I am missing; maybe I'm thinking Ubuntu somehow has locked any mysql access from a distant source. 

Ok it's no problem I'm writing the PHP code into a file:
<?php
@$dbh=mysql_connect ("localhost", "john" , "whatever") or die ('Incorrect password');
$query  = "CREATE DATABASE fire";
$result = mysql_query($query) or die ( "error :".mysql_error() );
?>

And guess what.. same error message: Can't create database 'fire' (errno: 13) 

If someone got a clue on why this is happening and how to fix this that would be great!! thanks!!

---

### Post by Necromantis on 2007-11-14
Finally found the problem.. the mysql data folder has to be on o=rwx to work.

2nd time I have to set a folder on o=rwx which I am told isn't a good thing.. but then I have no other options! 

Ubuntu server is supposed to be setup to work after the install but it's not the case at all.

---


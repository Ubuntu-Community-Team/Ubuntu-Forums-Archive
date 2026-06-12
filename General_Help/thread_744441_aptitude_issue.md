---
title: "aptitude issue"
date: 2008-04-03
forum: General Help
---

### Post by adam35413 on 2008-04-03
I have recently started using a Ubuntu 7.10 AMI for EC2.  When I went to start installing software, everything was fine when I installed php, lame, ruby, etc.  However, when I went to install mySQL, I got the following error:

```
sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0 
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.3MB/36.4MB of archives. After unpacking 107MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err http://us.archive.ubuntu.com gutsy-updates/main mysql-common 5.0.45-1ubuntu3.1
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com gutsy-security/main mysql-common 5.0.45-1ubuntu3.1
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main libmysqlclient15off 5.0.45-1ubuntu3.1
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main mysql-client-5.0 5.0.45-1ubuntu3.1
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main mysql-server-5.0 5.0.45-1ubuntu3.1
  404 Not Found
Err http://security.ubuntu.com gutsy-security/main mysql-server 5.0.45-1ubuntu3.1
  404 Not Found
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.1_all.deb: 404 Not Found
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

My sources.list file looks like this:

```
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

I have also tried installing via apt-get to no avail.  I have run update and upgrade for both apt-get and aptitude.

Does anyone have any ideas?

---

### Post by aysiu on 2008-04-03
It looks as if the server is down. Try a mirror or try again another time.

US mirror:
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

UK mirror:
[http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com)

Original site:
[http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by kellemes on 2008-04-03
Edit: mirror is not down.

Can you please try the following?
```
sudo apt-get -f install
```

After that try again..

---

### Post by bapoumba on 2008-04-03
Looks ike the us repos are down. Please try to remove the "us." in your sources.list.
```
sudo aptitude update
```
and try to install the packages again.

---

### Post by adam35413 on 2008-04-03
It doesn't to appear that the repos are down, since security.ubuntu.com and us.archive.ubuntu.com are both valid addresses when I try to navigate to them.

I tried running 
```
sudo apt-get -f install
```

and I got this: 

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libdbi-perl libplrpc-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Those are just some packages that got installed before mysql blew up, so that doesn't appear to be the issue.

Any other thoughts?  Does the address [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.1_all.deb) look right?  I tried to just go to that address and got a 404 error which seems to indicate that the path is wrong since the server is still up.

---

### Post by adam35413 on 2008-04-03
I just updated my source list to remove the "us." and now it appears to be working.  It appears to be a discrepancy between where mysql lives in us.archive.ubuntu.com and the main archive.

---

### Post by kellemes on 2008-04-03
path wrong indeed..

---

### Post by bapoumba on 2008-04-03
Ah okay :)
I just installed mysql-server to check it out, and it worked.. I was quite confused.

---

### Post by kellemes on 2008-04-03
I'm still confused..
But glad it works.

---

### Post by bapoumba on 2008-04-05
I have not investigated. Could it be that the repos where out of sync for dependencies, for ex?

---


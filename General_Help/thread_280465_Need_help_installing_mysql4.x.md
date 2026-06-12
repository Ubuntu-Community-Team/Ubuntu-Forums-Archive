---
title: "Need help installing mysql4.x"
date: 2006-10-19
forum: General Help
---

### Post by derkmerkin on 2006-10-19
Hello this is my fist post on the Ubuntu forums. I have a database servre machine that all it does it host the database. It was runnign gentoo, but somethign happened to it and it would no longer boot sying that something was wrong with the filesystem. Many fcsks later with no luck fixing it i decided to install the ubuntu server distro(6.06.1). 

After i got everything running(ssh, mysql, vsftp, etc..) i started to import the data fromt he old server onto the new one. The old server ran mysql 4.0.1x i believe. The inventory application that i wrote has a table named "release", release is now a keyword in mysql 5.0. I have been pulling my hair out trying to figure out how to install a 4.x version of mysql so that i dont have to dig through the app finding all references to release.

Lookign on the forums i hve seen people say that 
```
sudo aptitude purge mysql-server mysql-common mysql-client && sudo aptitude install mysql-client-4.1 mysql-server-4.1
``` should work. Instead i get a message
```
Note: selecting "mysql-client-5.0" instead of the
      virtual package "mysql-client-4.1"
Note: selecting "mysql-server-5.0" instead of the
      virtual package "mysql-server-4.1"
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl mysql-common perl perl-doc perl-modules
The following packages have been kept back:
  linux-image-server
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-common mysql-server-5.0 perl perl-doc
  perl-modules

```

It wants to install 5.0!! Please help!

I am running this machine as a headless server with no X, kde/gnome or any graphical environment. So a command line solution would be greatly appreciated.

D.

---

### Post by mjziegle on 2006-10-19
I had to revert back to 4.1 since mythtv 0.18 in the repos requires it instead of 5.0

to do this I ran 

sudo apt-get remove mysql-server --purge 

then ran 

sudo apt-get install mysql-server-4.1

You can use the '-s' flag to simulate to make sure you are getting the right packages.  

This sounds like a repo problem though.  Use apt-cache show  mysql-server-4.1 to learn more info.  You need the 'universe' enabled.

---

### Post by derkmerkin on 2006-10-20
That was it, got everything working perfectly. Thank you!

---


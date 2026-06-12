---
title: "Unable to install Zoneminder Ubuntu 14.04"
date: 2015-12-31
forum: General Help
---

### Post by morrissilas on 2015-12-31
I'm sorry if this has been posted before but I am unable to get Zoneminder to work at all on any version of Ubuntu I have tried. I originally started with Linux Mint 13 and couldn't get that to work after researching online and trying suggestions from other people. So I tried Linux Mint 17.3 since that was based on Ubuntu 14 and [Zoneminder has a guide for installing on Ubuntu 14]("http://zoneminder.readthedocs.org/en/latest/installationguide/ubuntu.html#easy-way-install-zoneminder-from-a-package-ubuntu-14-x"). But that was giving me the same error. After messing around and trying some things for a few hours, I wasn't getting anywhere. So I thought I would try just regular Ubuntu 14.04 because maybe Mint is a bit too different somehow or something. I don't know, I'm a noob at Linux. I have an old desktop that I have used for streaming Steam games that runs Ubuntu 14 so I'm not entirely unfamiliar with Ubuntu. Piece of cake right? Nope. Ubuntu 14 is giving me the same errors I was getting before. I'm about ready to smash things, I'm so frustrated. Here is what I'm working with:

old Dell Lattitude E5510 with new WD Caviar Black 750 GB hard drive, 4 GBs RAM. The OS runs perfectly fine as far as I can tell, no problems booting, no problems installing the OS, no problems connecting to wifi or anything. Figured this would be a good device to just keep running in a closet to monitor IP cameras. Of course, it won't be on wifi once it's set up.

Here is my problem. Whenever I get to this line in the installation:

morris@morris-security:~$ [B]sudo apt-get install zoneminder

[/B]I always get this as output:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  mysql-server mariadb-server
The following NEW packages will be installed:
  zoneminder
0 upgraded, 1 newly installed, 0 to remove and 229 not upgraded.
Need to get 1,036 kB of archives.
After this operation, 8,963 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/iconnor/zoneminder/ubuntu/](http://ppa.launchpad.net/iconnor/zoneminder/ubuntu/) trusty/main zoneminder amd64 1.28.1-trusty-2 [1,036 kB]
Fetched 1,036 kB in 2s (506 kB/s)     
Selecting previously unselected package zoneminder.
(Reading database ... 170648 files and directories currently installed.)
Preparing to unpack .../zoneminder_1.28.1-trusty-2_amd64.deb ...
Unpacking zoneminder (1.28.1-trusty-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up zoneminder (1.28.1-trusty-2) ...
mysql not found, assuming remote server.
DBI connect('database=zm;host=localhost','zmuser',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5/ZoneMinder/Config.pm line 91.
Can't connect to db at /usr/share/perl5/ZoneMinder/Config.pm line 100.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 33.
Compilation failed in require at /usr/bin/zmpkg.pl line 37.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 37.
ZoneMinder is stopped
invoke-rc.d: initscript zoneminder, action "status" failed.
Starting ZoneMinder: DBI connect('database=zm;host=localhost','zmuser',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5/ZoneMinder/Config.pm line 91.
Can't connect to db at /usr/share/perl5/ZoneMinder/Config.pm line 100.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 33.
Compilation failed in require at /usr/bin/zmpkg.pl line 37.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 37.
failure


invoke-rc.d: initscript zoneminder, action "start" failed.
dpkg: error processing package zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
morris@morris-security:~$ 

This happens no matter what I do. It is never able to install no matter what. I have tried:

sudo dpkg -r zoneminder 
sudo apt-get -f install 
sudo apt-get update 
sudo apt-get upgrade

And it still throws an error. I tried [this installation guide for an older Ubuntu]("https://wiki.zoneminder.com/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.26.5_the_easy_way") and that didn't work either.

Any help would be greatly appreciated. I have seen other posts from long ago with similar problems but the suggestions in those posts do not resolve my issue. I am willing to try older versions of Ubuntu, older versions of Zoneminder, anything to just get it working. My next step is try Ubuntu 12.04 and see if that works.

---

### Post by bab1 on 2015-12-31
It looks like you need to install the MySQL database first.  The Ubuntu package includes MySQL, but the ZM version is 1.26  See ```

Setting up zoneminder (1.28.1-trusty-2) ...
[COLOR="#FF0000"]**mysql not found, assuming remote server.**[/COLOR]
DBI connect('database=zm;host=localhost','zmuser',...) failed: [COLOR="#FF0000"]**Can't connect to local MySQL server**[/COLOR] through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5
```

---

### Post by yancek on 2015-12-31
The Zoneminder site at the link below specifically states the following:

> ZoneMinder also requires MySQL and PHP, and is enhanced by a webserver such as Apache

So you should install Apache, Mysql and php before installing Zoneminder.

[https://zoneminder.com/](https://zoneminder.com/)

The link below explains installing it on Ubuntu 14.04 Server version.  Not sure if there is much difference to a Desktop version but the info should be useful.

[https://wiki.zoneminder.com/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way](https://wiki.zoneminder.com/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way)

---

### Post by morrissilas on 2015-12-31
Thanks for this. For some reason I missed all of that and drove myself mad. I appreciate the help

---

### Post by Swagman on 2015-12-31
Ironically I've just succeeded in installing this.  I ended up going through the "install the hard-way" and it works.

What *doesn't* work is what I installed it for in the first place !!

That was to control my DVR which runs embedded Linux but some moron hard coded it to need Active X to "Desktop" remote connect (Internet Explorer). I was getting peed off having to load Win 7 in VirtualBox and was hoping that ZoneMinder would do the job.

After failing to connect, I googled it and it's a known issue

Bah !

My DVR is [** THIS**](http://www.amazon.co.uk/dp/B014R01UGG/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=3GECW62LBTENA&coliid=I35H08XK5BHZIA&psc=1) one (1500 TVL no longer available)

[Edit]

Here's a screeny running on my sys (15:10)

[http://i.imgur.com/8VeW0A0.jpg](http://i.imgur.com/8VeW0A0.jpg)

And in VB

[http://i.imgur.com/tN955fW.jpg](http://i.imgur.com/tN955fW.jpg)

btw.. to login type... "  [http://localhost/zm/index.php](http://localhost/zm/index.php)  " in your browsers address bar

---

### Post by bab1 on 2015-12-31
> **morrissilas said:**
> Thanks for this. For some reason I missed all of that and drove myself mad. I appreciate the help
Don't beat yourself up.  The instructions are not all that clear.

---


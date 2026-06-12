---
title: "Problem installing NFS"
date: 2007-11-01
forum: General Help
---

### Post by BrokenBrick on 2007-11-01
Originally I had a problem trying to install NFS through apt, and now I am having the same problem installing lm-sensors.  Here is the error output apt gives me

```
brokenbrick@blackie:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4 python2.4-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nfs-common (1:1.1.1~git-20070709-3ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lm-sensors (1:2.10.4-1ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing lm-sensors (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of xsensors:
 xsensors depends on lm-sensors; however:
  Package lm-sensors is not configured yet.
dpkg: error processing xsensors (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sensord:
 sensord depends on lm-sensors; however:
  Package lm-sensors is not configured yet.
dpkg: error processing sensord (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-common
 lm-sensors
 xsensors
 sensord
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ghpearson on 2007-11-01
I have a similar problem with APT.  I current have Kubuntu on AMD64 on a fresh install 7.10.  I was running adept manager to install some packages and it failed with a popup message about dependencies not met or package would break dependences.  Now when i try to install new packages i get the same message.  Here is the excerpt:

root@george-desktop:~# php5
The program 'php5' is currently not installed.  You can install it by typing:
apt-get install php5-cli
bash: php5: command not found
root@george-desktop:~# apt-get install php5-cli
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cli php5-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2839kB of archives.
After unpacking 6545kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main php5-common 5.2.3-1ubuntu6 [222kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main php5-cli 5.2.3-1ubuntu6 [2617kB]
Fetched 2839kB in 18s (157kB/s)
Selecting previously deselected package php5-common.
(Reading database ... 96795 files and directories currently installed.)
Unpacking php5-common (from .../php5-common_5.2.3-1ubuntu6_amd64.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.2.3-1ubuntu6_amd64.deb) ...
Setting up php5-common (5.2.3-1ubuntu6) ...
Setting up php5-cli (5.2.3-1ubuntu6) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing php5-cli (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have performed searches for ucf and it looks to be integrated into apt as a version controll system for upgrading configuration files.
my bash scripting is rusty, but i looked at line 351 in /usr/bin/ucf and it looks like it runs getopt to return some command line options to execute.

---

### Post by ghpearson on 2007-11-01
Ok... Long and Short...  Short:  I got it working.
Long:
UCF was not the problem... getopt missing was the problem: big problem.

Background:  I'm on an AMD64 architecture and I wanted to get Flash working on Firefox 64bit.
So i followed a google search article about installing 32bit environment to get nspluginwrapper installed.
Part of the dependencies of the 32bit environment was Linux32.
It collides with the util-linux package and ask you a very pointed question about blowing up your system and Do you know what you are doing answer Yes do it anyway; which i did ;(

So the fix was to run:

sudo apt-get install util-linux

when it asks you about removing linux32 answer yes.

that should stablize you apt scripts so you can perform adds and removes.
Hope this helps.

---

### Post by MewRS on 2008-01-12
Thank You A Lot!!!

You Saved My Life!

---


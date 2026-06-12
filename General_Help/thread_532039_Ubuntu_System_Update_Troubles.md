---
title: "Ubuntu System Update Troubles"
date: 2007-08-22
forum: General Help
---

### Post by SilasleCake on 2007-08-22
Hello,

For the past month or so I have not been able to install the system updates on my computer. I didn't really pay much attention to it because I haven't been using this computer much but yesterday I delved into the problem to try to understand what was wrong. 

Every time I try to install an update package, I get this error message:

```
E: /var/cache/apt/archives/(name of the package) failed in buffer_read(fd)
```

I tried to install these packages through Synaptic instead, but I got the same error. I tried removing all cached files in  (/var/cache/apt/archives), and downloaded them again, but that did not work either. Then I did some searches on the forums and on the web to see if there was anything about it, and I came across[ this]("http://ubuntuforums.org/archive/index.php/t-290848.html") post in the forum archives.
**dgandhi** replied:
 > 
I have the same problem after update, only i have it with libnss3, and any attempt to install or remove anything, even libnss3 results in the same issue.

I have tracked it down all the way to dpkg, wich is the program from which the error originates. dpkg will not even allow a reinstall of the offending package.

Does any body know:

1) a back end (dpkg) fix for this
2) which ubuntu package SHOULD catch/fix this error, to which we can submit a bug report.


However, this went unanswered (it is from November 2006). 

Could anyone shed some light on this problem? Any help would be appreciated.

---

### Post by bapoumba on 2007-08-22
Hello!
[http://ubuntuforums.org/showthread.php?t=352766]("http://ubuntuforums.org/showthread.php?t=352766")
There may be a solution there.

---

### Post by SilasleCake on 2007-08-22
thanks for the link, but I tried the three ideas listed on that page, but with no success:

-Running
```
sudo dpkg -configure -a
sudo apt-get autoclean
sudo apt-get update
```

-Changing my sources.list.

-Running
```
sudo touch /forcefsck
```

I actually thought the last one might work, seeing as it had for **ufa**, but when I booted the computer, it checked my disk but did not seem to find a problem and continued booting. 

However, I remember many times when I booted and the hard drive was forced to be checked (the periodical check, after 30 or so boots I think) that sometimes errors appeared on the disk. Unsure what to do about the errors, I just rebooted Ubuntu a few times in safe mode, and it usually ended up booting normally after one or two tries...

Is it possible that my hard drive has a problem that is not being detected properly by fsck?

By the way, is fsck the same thing that checks one's disk periodically when the computer boots.

---

### Post by bapoumba on 2007-08-22
Yes, fsck runs periodically (every 30 or so reboots). By creating the forcefsck file, you forced a check at next boot.
I would have bet, reading the thread, that it would solve your problem...

/me goes to dig a little more.

---

### Post by bapoumba on 2007-08-22
Are you using a CD to update/upgrade?
Could you post your sources.list?

---

### Post by SilasleCake on 2007-08-22
I am simply using the "update manager" to update my system, downloading the files off the internet.

Here is my sources.list:
```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
```

---

### Post by bapoumba on 2007-08-22
Your source.list is fine. I'm digging...

---

### Post by bapoumba on 2007-08-22
Do all packages bring up the error?
Please run:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
and post the complete error message (with package names on the error).

---

### Post by SilasleCake on 2007-08-22
I have not exactly checked if it happens with each package. I have tried with several individually (say 10), and none have worked.

I just did some delving of my own to provide some more information about my problem and found that when I try to install any package (not just updates), it does not work either, and I receive the same error message.

Here is the error code that I got when I ran your two commands
```
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing amarok (--remove):
 failed in buffer_read(fd): files list for package `tetex-extra': Input/output error
Errors were encountered while processing:
 amarok
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Thanks for all the help that you have provided so far!

---

### Post by bapoumba on 2007-08-22
Okay, wild shot. Do you have enough room on your partitions? Please run:
```
df -H
```

Edit: other than that, all I can find are comments related to failing hardware...

---

### Post by SilasleCake on 2007-08-23
None are used up more than 22 per cent!

---

### Post by bapoumba on 2007-08-23
I did read a lot of stuff last night, based on the errors you get. It's either related to failing hardware, md5sums or full partitions. I do not quite get it, I'm sorry :(

If you have other errors, please paste them in, we'll give them a shot.

---


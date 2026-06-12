---
title: "Need advice working on an SRU request for abiword in Precise"
date: 2012-10-21
forum: General Help
---

### Post by kansasnoob on 2012-10-21
Since Quantal testing is out of the way I'm trying to work on a request to upgrade 'abiword' in Precise which is an LTS release. In fact images are already being built and listed on the QA Tracker for 12.04.2 which is due the end of January:

[http://iso.qa.ubuntu.com/qatracker/milestones/204/builds](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds)

The reason(s) are mostly mentioned here:

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

And here:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

There are other bug reports:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/991399](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/991399)

In every case Martin Sevior, the package maintainer says:

> As maintainer of abiword I urge you to switch to abiword-2.8.6. Debian
testing has moved on to 2.9.3 which is a considerable improvement of
2.9.2 but it still contains many bugs. On the other hand
Debian-testing is for people who want to help software projects by
providing feedback rather than have code that "Just Works".
I think that most Ubtuntu users are in this category though.

I'd first requested that we downgrade to abiword 2.8.6 for 12.04.1 but I found that was not possible, however Dmitry Smirnov introduced a lot of bug fixes in the Quantal version so I think I should request that the Quantal version be introduced into Precise proposed updates.

I have read the SRU process:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

And I'd think the request does meet these guidelines:

> Bugs which do not fit under above categories, but (1) have an obviously safe patch and (2) affect an application rather than critical infrastructure packages (like X.org or the kernel). 

But due to limitations resulting from age and illness I feel like a one-legged man in a butt-kicking contest :oops:

One of the greatest limitations is my lack of ability to use IRC chat, and that seems to be the most highly recommended method of asking for development help.

****************

Anyway I've used zsync to update my Ubuntu and Xubuntu Precise test images (abiword is a native app in Xubuntu but not natively installed in Ubuntu) so in the next day or so I'm going to install both, and then try and install/upgrade them to the Quantal version of 'abiword' using this **[COLOR="Red"]incredibly risky procedure[/COLOR]**:

**[COLOR="Red"]NOTE[/COLOR]**: It bears repeating that this procedure is incredibly risky and **[COLOR="Red"]may blow up your installation[/COLOR]**!

#1: Install and upgrade the OS.

#2: Change the repos from Precise to Quantal via:

```
sudo sed -i s'/precise/quantal/g' /etc/apt/sources.list
```

#3: Update repos:

```
sudo apt-get update
```

**[COLOR="Red"]NOTE[/COLOR]**: Must NOT "upgrade" or "dist-upgrade"!

#4: Install/reinstall 'abiword':

```
sudo apt-get install abiword
```

#5: **[COLOR="Red"]Very important![/COLOR]** Change repos back to Precise via:

```
sudo sed -i s'/quantal/precise/g' /etc/apt/sources.list
```

And be sure to run:

```
sudo apt-get update
```

#6: Test using a combination of "apt" and "dpkg" commands to see if any package breakage or irregularities exist, eg;

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

#7: Parse the /var/log/apt history and terminal logs for any irregularities, and check the dependencies of each package installed or upgraded to see if any other packages may be broken (or suffer regressions) due to installing/upgrading those packages.

#8: Test the living day-lights out of 'abiword' itself :)

**********************

So, am I totally off-base :confused:

Any suggestions at all?

---

### Post by kansasnoob on 2012-10-22
I'm just testing this on Xubuntu Precise i386 20121021 and so far so good:

```
lance@lance-desktop:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  abiword-common abiword-plugin-grammar abiword-plugin-mathview
  fontconfig-config fonts-lyx libabiword-2.9 libfontconfig1 librdf0
Suggested packages:
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite
  redland-utils
The following NEW packages will be installed:
  fonts-lyx
The following packages will be upgraded:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  fontconfig-config libabiword-2.9 libfontconfig1 librdf0
8 upgraded, 1 newly installed, 0 to remove and 1155 not upgraded.
Need to get 5,201 kB of archives.
After this operation, 1,914 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Now to say yes and see what blows up :)

---

### Post by kansasnoob on 2012-10-22
That seemed to work fine in Xubuntu. I tested some documents that I knew were problematic in the Precise version of abiword and they seemed to work fine.

And the logs look fine to me.

apt/history:

```
Start-Date: 2012-10-21  23:53:03
Commandline: apt-get install abiword
Install: fonts-lyx:i386 (2.0.3-3, automatic)
Upgrade: librdf0:i386 (1.0.14-1, 1.0.15-1), abiword-common:i386 (2.9.2+svn20120213-1, 2.9.2+svn20120603-8), abiword:i386 (2.9.2+svn20120213-1, 2.9.2+svn20120603-8), abiword-plugin-mathview:i386 (2.9.2+svn20120213-1, 2.9.2+svn20120603-8), libfontconfig1:i386 (2.8.0-3ubuntu9.1, 2.10.1-0ubuntu3), fontconfig-config:i386 (2.8.0-3ubuntu9.1, 2.10.1-0ubuntu3), libabiword-2.9:i386 (2.9.2+svn20120213-1, 2.9.2+svn20120603-8), abiword-plugin-grammar:i386 (2.9.2+svn20120213-1, 2.9.2+svn20120603-8)
End-Date: 2012-10-21  23:53:33
```

apt/term:

```

Log started: 2012-10-21  23:08:09
Log ended: 2012-10-21  23:08:30

Log started: 2012-10-21  23:09:49
Log ended: 2012-10-21  23:09:49

Log started: 2012-10-21  23:11:47
Log ended: 2012-10-21  23:13:40

Log started: 2012-10-21  23:13:43
Log ended: 2012-10-21  23:13:44

Log started: 2012-10-21  23:15:46
Log ended: 2012-10-21  23:17:22

Log started: 2012-10-21  23:53:03
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 129038 files and directories currently installed.)
Preparing to replace libfontconfig1 2.8.0-3ubuntu9.1 (using .../libfontconfig1_2.10.1-0ubuntu3_i386.deb) ...
Unpacking replacement libfontconfig1 ...
Preparing to replace fontconfig-config 2.8.0-3ubuntu9.1 (using .../fontconfig-config_2.10.1-0ubuntu3_all.deb) ...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcd-filter-lcddefault.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf out of the way...
Moving obsolete conffile /etc/fonts/fonts.dtd out of the way...
Unpacking replacement fontconfig-config ...
Preparing to replace librdf0 1.0.14-1 (using .../librdf0_1.0.15-1_i386.deb) ...
Unpacking replacement librdf0 ...
Preparing to replace libabiword-2.9 2.9.2+svn20120213-1 (using .../libabiword-2.9_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement libabiword-2.9 ...
Preparing to replace abiword-plugin-grammar 2.9.2+svn20120213-1 (using .../abiword-plugin-grammar_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword-plugin-grammar ...
Selecting previously unselected package fonts-lyx.
Unpacking fonts-lyx (from .../fonts-lyx_2.0.3-3_all.deb) ...
Preparing to replace abiword-plugin-mathview 2.9.2+svn20120213-1 (using .../abiword-plugin-mathview_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword-plugin-mathview ...
Preparing to replace abiword-common 2.9.2+svn20120213-1 (using .../abiword-common_2.9.2+svn20120603-8_all.deb) ...
Unpacking replacement abiword-common ...
Preparing to replace abiword 2.9.2+svn20120213-1 (using .../abiword_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword ...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Setting up fontconfig-config (2.10.1-0ubuntu3) ...
Installing new version of config file /etc/fonts/fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-autohint.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-unhinted.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-vrgb.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-no-sub-pixel.conf ...
Installing new version of config file /etc/fonts/conf.avail/50-user.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-vbgr.conf ...
Installing new version of config file /etc/fonts/conf.avail/45-latin.conf ...
Installing new version of config file /etc/fonts/conf.avail/65-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/40-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/65-fonts-persian.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-bgr.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-rgb.conf ...
Installing new version of config file /etc/fonts/conf.avail/25-unhint-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-metric-aliases.conf ...
Installing new version of config file /etc/fonts/conf.avail/20-unhint-small-vera.conf ...
Installing new version of config file /etc/fonts/conf.avail/80-delicious.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-urw-aliases.conf ...
Removing obsolete conffile /etc/fonts/conf.avail/11-lcd-filter-lcddefault.conf ...
Removing obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf ...
Removing obsolete conffile /etc/fonts/fonts.dtd ...
Setting up libfontconfig1 (2.10.1-0ubuntu3) ...
Setting up librdf0 (1.0.15-1) ...
Setting up libabiword-2.9 (2.9.2+svn20120603-8) ...
Setting up abiword-common (2.9.2+svn20120603-8) ...
Setting up abiword (2.9.2+svn20120603-8) ...
Setting up abiword-plugin-grammar (2.9.2+svn20120603-8) ...
Setting up fonts-lyx (2.0.3-3) ...
Setting up abiword-plugin-mathview (2.9.2+svn20120603-8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2012-10-21  23:53:33
```

I'll probably wait to test it in Ubuntu until tomorrow :)

---

### Post by kansasnoob on 2012-10-22
That Xubuntu test worked so well I decided to go for broke and try my every day Ubuntu with a gazillion mods:

```
lance@lance-desktop:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgoffice-0.8-8-common libaiksaurusgtk-1.2-0c2a libaiksaurus-1.2-0c2a
  libabiword-2.8 libgoffice-0.8-8 libaiksaurus-1.2-data libwv-1.2-3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  abiword-common abiword-plugin-grammar abiword-plugin-mathview
  fontconfig-config fonts-lyx libabiword-2.9 libfontconfig1 librdf0
Suggested packages:
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite
  redland-utils
The following NEW packages will be installed:
  fonts-lyx
The following packages will be upgraded:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  fontconfig-config libabiword-2.9 libfontconfig1 librdf0
8 upgraded, 1 newly installed, 0 to remove and 1428 not upgraded.
Need to get 5,201 kB of archives.
After this operation, 1,914 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Looks OK other than obvious need to clean up some cruft from having used this install for several months :)

---

### Post by kansasnoob on 2012-10-22
Looks to have gone OK but I might want to see this later:

```
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main libfontconfig1 i386 2.10.1-0ubuntu3 [136 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal/main fontconfig-config all 2.10.1-0ubuntu3 [46.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal/main librdf0 i386 1.0.15-1 [114 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal/universe libabiword-2.9 i386 2.9.2+svn20120603-8 [1,942 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal/universe abiword-plugin-grammar i386 2.9.2+svn20120603-8 [16.7 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal/universe fonts-lyx all 2.0.3-3 [151 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ quantal/universe abiword-plugin-mathview i386 2.9.2+svn20120603-8 [84.6 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ quantal/universe abiword-common all 2.9.2+svn20120603-8 [1,569 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ quantal/universe abiword i386 2.9.2+svn20120603-8 [1,142 kB]
Fetched 5,201 kB in 10s (508 kB/s)                                             
(Reading database ... 261918 files and directories currently installed.)
Preparing to replace libfontconfig1 2.8.0-3ubuntu9.1 (using .../libfontconfig1_2.10.1-0ubuntu3_i386.deb) ...
Unpacking replacement libfontconfig1 ...
Preparing to replace fontconfig-config 2.8.0-3ubuntu9.1 (using .../fontconfig-config_2.10.1-0ubuntu3_all.deb) ...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcd-filter-lcddefault.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf out of the way...
Moving obsolete conffile /etc/fonts/fonts.dtd out of the way...
Unpacking replacement fontconfig-config ...
Preparing to replace librdf0 1.0.14-1 (using .../librdf0_1.0.15-1_i386.deb) ...
Unpacking replacement librdf0 ...
Preparing to replace libabiword-2.9 2.9.2+svn20120213-1 (using .../libabiword-2.9_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement libabiword-2.9 ...
Preparing to replace abiword-plugin-grammar 2.9.2+svn20120213-1 (using .../abiword-plugin-grammar_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword-plugin-grammar ...
Selecting previously unselected package fonts-lyx.
Unpacking fonts-lyx (from .../fonts-lyx_2.0.3-3_all.deb) ...
Preparing to replace abiword-plugin-mathview 2.9.2+svn20120213-1 (using .../abiword-plugin-mathview_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword-plugin-mathview ...
Preparing to replace abiword-common 2.9.2+svn20120213-1 (using .../abiword-common_2.9.2+svn20120603-8_all.deb) ...
Unpacking replacement abiword-common ...
Preparing to replace abiword 2.9.2+svn20120213-1 (using .../abiword_2.9.2+svn20120603-8_i386.deb) ...
Unpacking replacement abiword ...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up fontconfig-config (2.10.1-0ubuntu3) ...
Installing new version of config file /etc/fonts/fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-autohint.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-unhinted.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-vrgb.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-no-sub-pixel.conf ...
Installing new version of config file /etc/fonts/conf.avail/50-user.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-vbgr.conf ...
Installing new version of config file /etc/fonts/conf.avail/45-latin.conf ...
Installing new version of config file /etc/fonts/conf.avail/65-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/40-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/65-fonts-persian.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-bgr.conf ...
Installing new version of config file /etc/fonts/conf.avail/10-sub-pixel-rgb.conf ...
Installing new version of config file /etc/fonts/conf.avail/25-unhint-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-metric-aliases.conf ...
Installing new version of config file /etc/fonts/conf.avail/20-unhint-small-vera.conf ...
Installing new version of config file /etc/fonts/conf.avail/80-delicious.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-urw-aliases.conf ...
Removing obsolete conffile /etc/fonts/conf.avail/11-lcd-filter-lcddefault.conf ...
Removing obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf ...
Removing obsolete conffile /etc/fonts/fonts.dtd ...
Setting up libfontconfig1 (2.10.1-0ubuntu3) ...
Setting up librdf0 (1.0.15-1) ...
Setting up libabiword-2.9 (2.9.2+svn20120603-8) ...
Setting up abiword-common (2.9.2+svn20120603-8) ...
Setting up abiword (2.9.2+svn20120603-8) ...
Setting up abiword-plugin-grammar (2.9.2+svn20120603-8) ...
Setting up fonts-lyx (2.0.3-3) ...
Setting up abiword-plugin-mathview (2.9.2+svn20120603-8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

The devs may also find useful info in this.

---

### Post by kansasnoob on 2012-10-22
Well, I went for it:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1069634](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1069634)

Nothing fancy but hopefully a start :)

---

### Post by kansasnoob on 2012-10-22
Need to make a note of this upstream bug fix:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672149](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672149)

---

### Post by kansasnoob on 2012-10-29
I received a notification:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621/comments/38](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621/comments/38)

So hopefully we're gaining but please pay attention to the Precise specific changes:

[https://launchpad.net/~lubuntu-dev/+archive/staging?field.series_filter=precise](https://launchpad.net/~lubuntu-dev/+archive/staging?field.series_filter=precise)

You'll see they include package updates that have nothing to do with 'abiword':

[ATTACH]226352[/ATTACH]

So I'm going to write a testing script of sorts :)

Step #1; Add the PPA:

```
sudo add-apt-repository ppa:lubuntu-dev/staging
```

Step #2; update the repos:

```
sudo apt-get update
```

**Do NOT run any "upgrade" command!**

Step #3; install the Quantal version of 'abiword':

```
sudo apt-get install abiword
```

Step #4; disable that PPA in Software Sources:

[ATTACH]226399[/ATTACH]

Step #5; update the repos again:

```
sudo apt-get update
```

Then just continue testing 'abiword'.

---

### Post by kansasnoob on 2012-10-30
Upgrading via that PPA looks a tiny bit odd:

```
lance@lance-desktop:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  abiword-common libabiword-2.9
Recommended packages:
  abiword-plugin-grammar abiword-plugin-mathview
The following packages will be upgraded:
  abiword abiword-common libabiword-2.9
3 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 4,739 kB of archives.
After this operation, 1,191 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

But I need to do some more studying :)

I decided to see what happened with the "yes" switch:

```
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu/ precise/main libabiword-2.9 i386 2.9.2+svn20120603-8~precise1~ppa1 [1,974 kB]
Get:2 http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu/ precise/main abiword-common all 2.9.2+svn20120603-8~precise1~ppa1 [1,609 kB]
Get:3 http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu/ precise/main abiword i386 2.9.2+svn20120603-8~precise1~ppa1 [1,156 kB]
Fetched 4,739 kB in 10s (471 kB/s)                                             
(Reading database ... 124745 files and directories currently installed.)
Preparing to replace libabiword-2.9 2.9.2+svn20120213-1 (using .../libabiword-2.9_2.9.2+svn20120603-8~precise1~ppa1_i386.deb) ...
Unpacking replacement libabiword-2.9 ...
Preparing to replace abiword-common 2.9.2+svn20120213-1 (using .../abiword-common_2.9.2+svn20120603-8~precise1~ppa1_all.deb) ...
Unpacking replacement abiword-common ...
Preparing to replace abiword 2.9.2+svn20120213-1 (using .../abiword_2.9.2+svn20120603-8~precise1~ppa1_i386.deb) ...
Unpacking replacement abiword ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libabiword-2.9 (2.9.2+svn20120603-8~precise1~ppa1) ...
Setting up abiword-common (2.9.2+svn20120603-8~precise1~ppa1) ...
Setting up abiword (2.9.2+svn20120603-8~precise1~ppa1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Now to test a lot and pick my brain a little :)

---

### Post by kansasnoob on 2012-11-02
Still picking my little brain, and praying [-o<

I've been doing a lot of reinstalls and I don't want to lose this so I'm attaching a file.

[ATTACH]226570[/ATTACH]

---


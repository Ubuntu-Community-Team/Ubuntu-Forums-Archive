---
title: "Any tricks for getting software installed on Ubuntu 10.10"
date: 2013-01-09
forum: General Help
---

### Post by agrayray on 2013-01-09
I know the general answer is it not possible but I WOUlD REALLY like to install 10.10 again on my machine..and add the software I had previously....

I was using Ubuntu 10.10 on my machine Thinkpad T-410 since it came out and it by FAR the best OS I have ever used...and I loved it..and using my machine every day...

I had the following software on it:

Firefox,Flash - most used (50%)
VMware Workstation 7.1.5 - own install (40%)
other ten percent was:

mousepad
desktop recorder
cheese
wine 
geany
GIMP

Early December one website would not work with the Firefox I had..so I decided to upgrade to 12.04 and then 12.10 and back to 12.04...

I have used Unity and GNome classic both for several weeks...and sad to say it just is not nearly as good..

most importantly for me..I work off of a several USB hard drives and noticed that 12.x versions do not work well it...when I use the USB drive (mostly copying VMs and things..large files)...my whole system gets slow/choppy and most importantly I can not use my USB drives for anything else...

I also tried going back to 10.04 but for some reason it can not seem to play MP4, and MKV files well (with the restricted extras)....

so..my question is..does anyone know if i can get software installed on a new 10.10 distro...I know I can set the updates to update where the updates were cut off..which is fine with me..as I mostly only goto a few trusted sites (espn3 and foxsoccer) with firefox..and the rest I do in VMs...but I would really love to stick with Ubuntu and get back to a perfect environment....

I know I can add Firefox PPA to updates and that should work keeping FF updated..and probably can download most of the other software manually..but I not sure about restricted extras that I need...

can anyone pass some tricks/advice for me???

Thanks SO MUCH !!!

---

### Post by howefield on 2013-01-09
Set your sources.list to point to the old-releases repositories.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You'll can install what you could way back then.

I would recommend finding something more modern and currently supported though, with an updated kernel, ect,. they don't all come with Unity/Gnome ;)

---

### Post by TheFu on 2013-01-09
10.10 is out of support, so running it is a **terrible** idea.  Programs are not being compiled to work with that release any more, so do not ever expect any new software. This is critical for web browsers.  Running Firefox without the constant security patches is crazy, IMHO.

I would strongly suggest another option.
* Load 12.04 LTS. It will be supported with security patches until early 2017, though in about another year, new programs will stop being compiled for it by software developers.  Ubuntu 10.04 is having that issue now with Firefox.
* Install one of the 20+ different windowing environments until you find the one that you like. There are a bunch.
* Realize the the GUI is just a program and NOT the operatiing system. There is no need to downgrade to an older, unsupported, release just to get that old desktop back.

You can still load Gnome2. Heck, I sometimes still run the same window manager that I used in 1996 (fvwm) on my desktop.

Good luck! I hope this was clear.

---

### Post by agrayray on 2013-01-09
Thanks very much for the replies!

I do understand your concerns, however for me I just want to be happy and have a well running machine...so at this moment..10.10 is for me...

that said..i tried the approach of editing my sources.list file but it seems i need a little more help...

I used a writeup found here:  [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

and...

basically i opened the sources.list file in gedit (using sudo and did a search and replace 

from:  us.archive.ubuntu.com/ubuntu/
to : help.ubuntu.com/community/EOLUpgrades

which looked right for me as I did a similar trick for updates before...

however it didnt seem to work..

I could not install from software center, cmd line using apt-get install, or package manager...like i did before .and the synaptic package manager seems to list the EOLUpgrade url...but I get connection errors from the software manager and get pkg not found errors from cmd line like:

rei@ubuntu:/etc/apt$ sudo apt-get install mousepad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mousepad


Did I do something wrong or need something more?

Below is my sources.list file if it helps...

```
[FONT=Courier New]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick main restricted
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates main restricted
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick universe
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick universe
deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates universe
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick multiverse
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick multiverse
deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates multiverse
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-backports main restricted universe multiverse
deb-src [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse[/FONT]
```

---

### Post by agrayray on 2013-01-10
Update..fixed this on my own..as I soon realized that:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

is not the url to use in the sources.list but rather instructions on how to edit it (was unclear before)...

anyway..I set all my urls to the old.releases url and got it working.

For some reason I the software center seemed to hang after I authenticated..and showed no status for installing or finishing...but once I closed it I noticed the software was there.

After two tries with the software center, I am installing the rest via the command and that seems to work just fine..

so moral for me..after changing the sources.list file...if you install the software via the command you should be all set.

Thank very much for the help!

---

### Post by CharlesA on 2013-01-10
You probably needed to update the repo index, but I have little experience if software center does that automatically or not.

---

### Post by mc4man on 2013-01-10
> **CharlesA said:**
> You probably needed to update the repo index, but I have little experience if software center does that automatically or not.

Was always under impression that it didn't, I know it won't show updates for installed packages as screen.

Pretty easy to check - will have to do so some time soon (just updated sources so can't atm..

---

### Post by agrayray on 2013-01-10
Ok..so because everything went so great..I have one final question...

anyone know how I can install skype that was with 10.10 repo?

Not sure if this was from the partner urls in the sources or what..I do know it was a beta but I can not recall that version..I really would like that specific version..besides it seems from the skype site..you can only get versions that do not work for 10.10 64 bit at least from there main downloads...

I downloaded all the .deb files I could from the skype site and tried to install them but got errors...

I did find a url you can download old skype versions and download the .deb files from [http://download.skype.com/linux/](http://download.skype.com/linux/)
but you have to know the version number and hit by brute force url..as the they dont allow a index...???

[http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_amd64.deb](http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_amd64.deb)

does anyone have the .deb file or know what the version of skype that was with the 10.10 64 bit distro??  

 (havent found via google so far) it...or at least one that works on 10.10...if not no big deal as again I can run everything else I need in VMs but just figured I would go for broke here..as I plan to get this as far I can to my old machine..ghost it for later.

other than skype I have everything like it was before...?

Thanks again!!!

---

### Post by agrayray on 2013-01-10
> **CharlesA said:**
> You probably needed to update the repo index, but I have little experience if software center does that automatically or not.


yeah..that was the trick...once the repo was re-set the software center works as normal...so you dont need to do everything from command line...

thanks for the tip!

---

### Post by howefield on 2013-01-10
> **agrayray said:**
> I downloaded all the .deb files I could from the skype site and tried to install them but got errors...

WWhat was the error when you tried to install the package marked 10.04 ?

This one... skype-ubuntu-lucid_4.1.0.20-1_i386.deb

> ...or know what the version of skype that was with the 10.10 64 bit distro??

I_think_it was Skype version 2.2.0.35-0maverick1

---

### Post by mc4man on 2013-01-10
> **howefield said:**
> 
I_think_it was Skype version 2.2.0.35-0maverick1
That one is available in Launchpad - you'd pick your arch under "Builds"            
[https://launchpad.net/ubuntu/+source/skype/2.2.0.35-0maverick1](https://launchpad.net/ubuntu/+source/skype/2.2.0.35-0maverick1)

---

### Post by agrayray on 2013-01-10
> **howefield said:**
> WWhat was the error when you tried to install the package marked 10.04 ?

This one... skype-ubuntu-lucid_4.1.0.20-1_i386.deb



I_think_it was Skype version 2.2.0.35-0maverick1

I didnt get errors on the install per see..but rather runtime errors.  That said, I was able to install the 64 bit versions from the launchpad just fine...In case it helps anyone here is exactly what I did for both versions...

A. Working - Launchpad .deb Install

1. download the tar from the launchpad link
2. extra it and use the 64 bit deb in my case
3. run the following from terminal (history below)

5```
  sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb (failed because it needed the following)
    6  sudo apt-get install lib32stdc++6
    7  sudo apt-get install lib32asound2
    8  sudo apt-get install ia32-libs
    9  sudo apt-get install libc6-i386
   10  sudo apt-get install lib32gcc1
   11  sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb 
```


B. Failed - Skype Website 10.04 32 bit install

1. Download the 32 bit (only one available on Jan 10 2013) version deb for 10.04 (Lucid)
2. Ran the following from the terminal

```
rei@ubuntu:~/Downloads$ sudo dpkg -i --force-architecture skype-ubuntu-lucid_4.1.0.20-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 141280 files and directories currently installed.)
Preparing to replace skype 4.1.0.20-1 (using skype-ubuntu-lucid_4.1.0.20-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus is not installed.
 skype depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network is not installed.
 skype depends on libqt4-webkit (>= 4:4.5.3); however:
  Package libqt4-webkit is not installed.
 skype depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml is not installed.
 skype depends on libqtcore4 (>= 4:4.6.1); however:
  Package libqtcore4 is not installed.
 skype depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 skype
rei@ubuntu:~/Downloads$ sudo apt-get install libqt4-dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-xml libqtcore4
The following NEW packages will be installed:
  libqt4-dbus libqt4-xml libqtcore4
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,211kB of archives.
After this operation, 8,921kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libqtcore4 amd64 4:4.7.0-0ubuntu4.4 [1,839kB]
Get:2 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libqt4-xml amd64 4:4.7.0-0ubuntu4.4 [135kB]
Get:3 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libqt4-dbus amd64 4:4.7.0-0ubuntu4.4 [237kB]
Fetched 2,211kB in 5s (407kB/s)
Selecting previously deselected package libqtcore4.
(Reading database ... 141280 files and directories currently installed.)
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Setting up libqtcore4 (4:4.7.0-0ubuntu4.4) ...
Setting up libqt4-xml (4:4.7.0-0ubuntu4.4) ...
Setting up libqt4-dbus (4:4.7.0-0ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rei@ubuntu:~/Downloads$ sudo apt-get install libqt4-network
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libqt4-network
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 487kB of archives.
After this operation, 1,741kB of additional disk space will be used.
Get:1 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libqt4-network amd64 4:4.7.0-0ubuntu4.4 [487kB]
Fetched 487kB in 2s (213kB/s)         
Selecting previously deselected package libqt4-network.
(Reading database ... 141339 files and directories currently installed.)
Unpacking libqt4-network (from .../libqt4-network_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Setting up libqt4-network (4:4.7.0-0ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rei@ubuntu:~/Downloads$ sudo apt-get install libqt4-webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaudio2 libdirectfb-1.2-9 libmng1 libmodplug1 libmpcdec6 libphonon4
  libqtgui4 libqtwebkit4 libts-0.0-0 libxcb-shape0 libxcb-xv0 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x phonon
  phonon-backend-xine tsconf
Suggested packages:
  nas qt4-qtconfig gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg
  phonon-backend-gstreamer phonon-backend-vlc phonon-backend-mplayer
The following NEW packages will be installed:
  libaudio2 libdirectfb-1.2-9 libmng1 libmodplug1 libmpcdec6 libphonon4
  libqt4-webkit libqtgui4 libqtwebkit4 libts-0.0-0 libxcb-shape0 libxcb-xv0
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  phonon phonon-backend-xine tsconf
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.2MB of archives.
After this operation, 44.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://old-releases.ubuntu.com/ubuntu/ maverick/main libaudio2 amd64 1.9.2-3 [85.0kB]
Get:2 http://old-releases.ubuntu.com/ubuntu/ maverick/main tsconf all 1.0-7build1 [12.8kB]
Get:3 http://old-releases.ubuntu.com/ubuntu/ maverick/main libts-0.0-0 amd64 1.0-7build1 [29.1kB]
Get:4 http://old-releases.ubuntu.com/ubuntu/ maverick/main libdirectfb-1.2-9 amd64 1.2.10.0-4ubuntu2 [1,197kB]
Get:5 http://old-releases.ubuntu.com/ubuntu/ maverick/main libmng1 amd64 1.0.10-1 [233kB]
Get:6 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libmodplug1 amd64 1:0.8.8.1-1ubuntu1.3 [179kB]
Get:7 http://old-releases.ubuntu.com/ubuntu/ maverick/main libmpcdec6 amd64 2:0.1~r459-1 [34.7kB]
Get:8 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/main libqtgui4 amd64 4:4.7.0-0ubuntu4.4 [4,052kB]
Get:9 http://old-releases.ubuntu.com/ubuntu/ maverick/main libphonon4 amd64 4:4.7.0really4.4.2-0ubuntu1 [135kB]
Get:10 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxine1-bin amd64 1.1.18.1-4ubuntu4 [1,274kB]
Get:11 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxine1-misc-plugins amd64 1.1.18.1-4ubuntu4 [844kB]
Get:12 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxcb-shape0 amd64 1.6-1 [9,822B]
Get:13 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxcb-xv0 amd64 1.6-1 [13.6kB]
Get:14 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxine1-x amd64 1.1.18.1-4ubuntu4 [152kB]
Get:15 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxine1-console amd64 1.1.18.1-4ubuntu4 [46.8kB]
Get:16 http://old-releases.ubuntu.com/ubuntu/ maverick/main libxine1 amd64 1.1.18.1-4ubuntu4 [1,610B]
Get:17 http://old-releases.ubuntu.com/ubuntu/ maverick/main phonon-backend-xine amd64 4:4.7.0really4.4.2-0ubuntu1 [148kB]
Get:18 http://old-releases.ubuntu.com/ubuntu/ maverick/main phonon all 4:4.7.0really4.4.2-0ubuntu1 [10.1kB]
Get:19 http://old-releases.ubuntu.com/ubuntu/ maverick/main libqtwebkit4 amd64 2.0.0-0ubuntu1 [4,722kB]
Get:20 http://old-releases.ubuntu.com/ubuntu/ maverick-updates/universe libqt4-webkit amd64 4:4.7.0-0ubuntu4.4 [46.9kB]
Fetched 13.2MB in 23s (566kB/s)                                                
Selecting previously deselected package libaudio2.
(Reading database ... 141351 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.2-3_amd64.deb) ...
Selecting previously deselected package tsconf.
Unpacking tsconf (from .../tsconf_1.0-7build1_all.deb) ...
Selecting previously deselected package libts-0.0-0.
Unpacking libts-0.0-0 (from .../libts-0.0-0_1.0-7build1_amd64.deb) ...
Selecting previously deselected package libdirectfb-1.2-9.
Unpacking libdirectfb-1.2-9 (from .../libdirectfb-1.2-9_1.2.10.0-4ubuntu2_amd64.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.10-1_amd64.deb) ...
Selecting previously deselected package libmodplug1.
Unpacking libmodplug1 (from .../libmodplug1_1%3a0.8.8.1-1ubuntu1.3_amd64.deb) ...
Selecting previously deselected package libmpcdec6.
Unpacking libmpcdec6 (from .../libmpcdec6_2%3a0.1~r459-1_amd64.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Selecting previously deselected package libphonon4.
Unpacking libphonon4 (from .../libphonon4_4%3a4.7.0really4.4.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libxine1-bin.
Unpacking libxine1-bin (from .../libxine1-bin_1.1.18.1-4ubuntu4_amd64.deb) ...
Selecting previously deselected package libxine1-misc-plugins.
Unpacking libxine1-misc-plugins (from .../libxine1-misc-plugins_1.1.18.1-4ubuntu4_amd64.deb) ...
Selecting previously deselected package libxcb-shape0.
Unpacking libxcb-shape0 (from .../libxcb-shape0_1.6-1_amd64.deb) ...
Selecting previously deselected package libxcb-xv0.
Unpacking libxcb-xv0 (from .../libxcb-xv0_1.6-1_amd64.deb) ...
Selecting previously deselected package libxine1-x.
Unpacking libxine1-x (from .../libxine1-x_1.1.18.1-4ubuntu4_amd64.deb) ...
Selecting previously deselected package libxine1-console.
Unpacking libxine1-console (from .../libxine1-console_1.1.18.1-4ubuntu4_amd64.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.1.18.1-4ubuntu4_amd64.deb) ...
Selecting previously deselected package phonon-backend-xine.
Unpacking phonon-backend-xine (from .../phonon-backend-xine_4%3a4.7.0really4.4.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package phonon.
Unpacking phonon (from .../phonon_4%3a4.7.0really4.4.2-0ubuntu1_all.deb) ...
Selecting previously deselected package libqtwebkit4.
Unpacking libqtwebkit4 (from .../libqtwebkit4_2.0.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libqt4-webkit.
Unpacking libqt4-webkit (from .../libqt4-webkit_4%3a4.7.0-0ubuntu4.4_amd64.deb) ...
Processing triggers for man-db ...
Setting up libaudio2 (1.9.2-3) ...
Setting up tsconf (1.0-7build1) ...
Setting up libts-0.0-0 (1.0-7build1) ...
Setting up libdirectfb-1.2-9 (1.2.10.0-4ubuntu2) ...
Setting up libmng1 (1.0.10-1) ...
Setting up libmodplug1 (1:0.8.8.1-1ubuntu1.3) ...
Setting up libmpcdec6 (2:0.1~r459-1) ...
Setting up libqtgui4 (4:4.7.0-0ubuntu4.4) ...
Setting up libphonon4 (4:4.7.0really4.4.2-0ubuntu1) ...
Setting up libxine1-bin (1.1.18.1-4ubuntu4) ...
Setting up libxine1-misc-plugins (1.1.18.1-4ubuntu4) ...
Setting up libxcb-shape0 (1.6-1) ...
Setting up libxcb-xv0 (1.6-1) ...
Setting up libxine1-x (1.1.18.1-4ubuntu4) ...
Setting up libxine1-console (1.1.18.1-4ubuntu4) ...
Setting up libxine1 (1.1.18.1-4ubuntu4) ...
Setting up phonon-backend-xine (4:4.7.0really4.4.2-0ubuntu1) ...
Setting up phonon (4:4.7.0really4.4.2-0ubuntu1) ...
Setting up libqtwebkit4 (2.0.0-0ubuntu1) ...
Setting up libqt4-webkit (4:4.7.0-0ubuntu4.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rei@ubuntu:~/Downloads$ sudo apt-get install libqt4-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-xml is already the newest version.
libqt4-xml set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rei@ubuntu:~/Downloads$ sudo apt-get install libqtcore4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtcore4 is already the newest version.
libqtcore4 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rei@ubuntu:~/Downloads$ sudo apt-get install libqtgui4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtgui4 is already the newest version.
libqtgui4 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rei@ubuntu:~/Downloads$ sudo dpkg -i --force-architecture skype-ubuntu-lucid_4.1.0.20-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 141697 files and directories currently installed.)
Preparing to replace skype 4.1.0.20-1 (using skype-ubuntu-lucid_4.1.0.20-1_i386.deb) ...
Unpacking replacement skype ...
Setting up skype (4.1.0.20-1) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
```


3. launching it from menu gives error that skype is not there (it is)...and trying from command line fails too ..complaining of missing file...



```
rei@ubuntu:~/Downloads$ which skype
/usr/bin/skype
rei@ubuntu:~/Downloads$ cd /usr/bin
rei@ubuntu:/usr/bin$ cd skype
bash: cd: skype: Not a directory
rei@ubuntu:/usr/bin$ ls skype
skype
rei@ubuntu:/usr/bin$ ls -l skype
-rwxr-xr-x 1 root root 28692596 2012-11-01 01:29 skype
rei@ubuntu:/usr/bin$ skype
bash: /usr/bin/skype: No such file or directory
rei@ubuntu:/usr/bin$ ./skype
bash: ./skype: No such file or directory
rei@ubuntu:/usr/bin$ cp skype skype.test
cp: cannot create regular file `skype.test': Permission denied
rei@ubuntu:/usr/bin$ sudo cp skype skype.test
rei@ubuntu:/usr/bin$ ls skype
skype
rei@ubuntu:/usr/bin$ ls skype*
skype  skype.test
rei@ubuntu:/usr/bin$ ls -l skype*
-rwxr-xr-x 1 root root 28692596 2012-11-01 01:29 skype
-rwxr-xr-x 1 root root 28692596 2013-01-10 15:01 skype.test
rei@ubuntu:/usr/bin$ ./skype.test 
bash: ./skype.test: No such file or directory
rei@ubuntu:/usr/bin$ ./dummy
bash: ./dummy: No such file or directory
rei@ubuntu:/usr/bin$ sudo chmod 777 skype
rei@ubuntu:/usr/bin$ ./sk
skill       skype       skype.test  
rei@ubuntu:/usr/bin$ ./skype
bash: ./skype: No such file or directory
rei@ubuntu:/usr/bin$ 
```



Hope this helps..if anyone has major peformance issues with vmware workstation 9.x and USB drives like I did...

and...

thanks so much for ALL the help everyone...words really can not convey how GRATEFUL I am!!!

---

### Post by agrayray on 2013-01-10
For some reason..my pictures didnt post...attached failed and working screenshot here...

---


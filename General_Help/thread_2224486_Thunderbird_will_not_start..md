---
title: "Thunderbird will not start."
date: 2014-05-16
forum: General Help
---

### Post by Dave_Ryan on 2014-05-16
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

thunderbird -version
 Thunderbird 10.0.2

thunderbird -version
 Thunderbird 17.0.8

thunderbird -version
 Thunderbird 24.2.0


My general users can not start Thunderbird after a fresh build and a reboot. They get the "Thunderbird had a problem and crashed.... Quit Thunderbird or Restart Thunderbird" dialog box. Yet root user can start Thunderbird without issue.

During the build process I tested Thunderbird to be fine, even during apt-get -f install, apt-get upgrade, & /usr/bin/update-manager. Only after a reboot does it fail to start.

Please do not ask me to upgrade Ubuntu. I have tested up to 14.04 LTS, including ubuntu-gnome-14.04, and my users do not like the gnome panel versions in those releases. I am still working to get 14.04 gnome panels to be similar to 10.04. Until then, I have to use 10.04.

Please tell me what is going on. My older 10.04.4 work stations work fine with any version of Thunderbird. Just new builds.

Dave Ryan
<snip>
Senior System Administrator
Output Services, Inc.
Friday, May 16, 2014 1106 hrs MDT

---

### Post by pqwoerituytrueiwoq on 2014-05-16
have you tried a clean profile?
```
pkill -f thunderbird
mv .thunderbird .thunderbird-old
thunderbird &
```
does the user have read/write access to there .thunderbrd folder?

as for your issue with gnome-panel have you checked xubuntu out?
[[IMG]http://www.zimagez.com/avatar/screenshot-04152014-012037pm.png[/IMG]]("http://www.zimagez.com/zimage/screenshot-04152014-012037pm.php")

---

### Post by stalkingwolf on 2014-05-16
or Mint 13 Mate?

---

### Post by Dave_Ryan on 2014-05-16
Yes. I have done the new profile. It still fails. The users have read / write access to the .thunderbird directory. The "home" directory is mounted via NFS. Users can go to an older built work station and thunderbird works just fine. It's just these new builds.

I will look at xubuntu when time permits.  
 

Dave Ryan
[email]<removed>[/email]
Senior System Administrator
Output Services, Inc.
Friday, May 16, 2014 1156 hrs MDT

---

### Post by Dave_Ryan on 2014-05-16
> **stalkingwolf said:**
> or Mint 13 Mate?

Will look into it. But we are most familiar with Ubuntu.

---

### Post by pqwoerituytrueiwoq on 2014-05-16
linux mint is based on ubuntu, even uses the same software sources + a couple extra
mate is a recreation of gnome2, i have not checked its status in a couple years
looks like linux mint 17 mate is in the RC stage, so i would suggest checking that and xubuntu 14.04

---

### Post by Dave_Ryan on 2014-05-22
I figured out why thunderbird will not start. It happens after I install wine 1.4 and reboot.

These are the items installed for wine:

libc6_2.15-0ubuntu10.2_i386.deb
libc-bin_2.15-0ubuntu10.2_i386.deb
multiarch-support_2.15-0ubuntu10.2_i386.deb
libltdl7_2.4.2-1ubuntu1_i386.deb
libgphoto2-port0_2.4.13-1ubuntu1_i386.deb
libjpeg-turbo8_1.1.90+svn733-0ubuntu4_i386.deb
libjpeg8_8c-2ubuntu7_i386.deb
libgphoto2-2_2.4.13-1ubuntu1_i386.deb
libmpg123-0_1.12.1-3.2ubuntu1_i386.deb
libopenal-data_1.13-4ubuntu3_all.deb
libopenal1_1.13-4ubuntu3_i386.deb
wine1.4-i386_1.4-0ubuntu4_i386.deb
wine1.4_1.4-0ubuntu4_i386.deb
wine1.4-common_1.4-0ubuntu4_all.deb

While I install these debs thunderbird works fine. But once I reboot it will not start up.

One or more of these debs is breaking the operation of thunderbird. But I don't know which one it is. Without installing each one, one at at time and rebooting I will not find the culprit.

---

### Post by oldfred on 2014-05-22
While server version of 10.04 is still supported is part of issue that desktop version is not?

I also prefered the old menu system and have a 4:3 monitor so also prefer top & bottom panels.
So with 12.04 I installed fallback, and I have installed flashback into 14.04 and so far it seems to work, but I still am mostly in 12.04.

       [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
You can reset gnome-panel settings to default:
dconf reset -f /org/gnome/gnome-panel/
[URL="http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04"]http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04

[/URL]
 12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

[URL="http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04"]
[/URL]

---


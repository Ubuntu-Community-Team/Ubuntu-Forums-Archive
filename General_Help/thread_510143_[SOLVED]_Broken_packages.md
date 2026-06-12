---
title: "[SOLVED] Broken packages"
date: 2007-07-26
forum: General Help
---

### Post by upthelum on 2007-07-26
Pardon me if i'm in the wrong place but i get a message telling me i have broken packages when trying to install compiz-fusion. I did the - synaptic, edit, fix broken packages and it did nothing for the install. Is there another way to fix the packages or update the repositories, i was looking forward to fiddling with compiz...
I use a asus board with A8V-VM SE onboard graphics which i set to 128mb in bios, gig ram and athlon 64.
HELP

---

### Post by Richard Kut on 2007-07-27
You need to provide some more detail before we can get to a solution. In order to do that, please open a terminal and type:

sudo apt-get update

and then paste the output into this post.

---

### Post by upthelum on 2007-07-28
root@linuxhomepc:/# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 0s (5B/s)
Reading package lists... Done
root@linuxhomepc:/#

Thanks.

I also have a problem with the os somewhere as i dont have System > Preferences anywhere in the menu...

---

### Post by forestpixie on 2007-07-28
try to install compiz-fusion again and post the error output of that

---

### Post by upthelum on 2007-07-28
I ran
sh /path/to/file/CF Installer-Updater.sh
which asked me if i want to install or update which i chose to install, here's the rest:

root@linuxhomepc:/home/don/Desktop# sh /home/don/Desktop/CFInstaller-Updater.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Do you have any KDE packages installed?(y/n)y
Reading package lists... Done
Building dependency tree... Done
autoconf is already the newest version.
autotools-dev is already the newest version.
build-essential is already the newest version.
debhelper is already the newest version.
dpkg-dev is already the newest version.
g++ is already the newest version.
E: Couldn't find package g++-4.1
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex 'emerald*'
E: Couldn't find package emerald*
mkdir: cannot create directory `/root/compiz': File exists
Downloading Compiz Fusion and everything else required...
/home/don/Desktop/CFInstaller-Updater.sh: line 32: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 33: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 34: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 35: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 36: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 37: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 38: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 39: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 40: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 41: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 42: git: command not found
Did you get a message about gitfm?(y/n)n
Continuing...
Installing Compiz...
/home/don/Desktop/CFInstaller-Updater.sh: line 65: cd: /root/compiz/compiz: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 66: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing bcop...
/home/don/Desktop/CFInstaller-Updater.sh: line 74: cd: /root/compiz/bcop: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 75: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing libcompizconfig...
/home/don/Desktop/CFInstaller-Updater.sh: line 81: cd: /root/compiz/libcompizconfig: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 82: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing compizconfig-python...
/home/don/Desktop/CFInstaller-Updater.sh: line 88: cd: /root/compiz/compizconfig-python: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 89: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing ccsm...
/home/don/Desktop/CFInstaller-Updater.sh: line 95: cd: /root/compiz/ccsm: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-main...
/home/don/Desktop/CFInstaller-Updater.sh: line 102: cd: /root/compiz/plugins-main: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 103: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald...
/home/don/Desktop/CFInstaller-Updater.sh: line 109: cd: /root/compiz/emerald: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 110: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald-Themes...
/home/don/Desktop/CFInstaller-Updater.sh: line 116: cd: /root/compiz/emerald-themes: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 117: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-extra...
/home/don/Desktop/CFInstaller-Updater.sh: line 123: cd: /root/compiz/plugins-extra: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 124: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-unsupported...
/home/don/Desktop/CFInstaller-Updater.sh: line 130: cd: /root/compiz/plugins-unsupported: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 131: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Do you use a NVidia graphics card? If you press yes, a command will be executed (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) which might be needed to make window decorations work.(y/n)n
Skipping...
Installing Compiz Fusion Icon...
/home/don/Desktop/CFInstaller-Updater.sh: line 144: cd: /root/compiz/fusion-icon: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Completed
Warning: Do not delete the files that this script downloaded to your home folder. If you do so, update will not be possible.
Tip: In order to launch Compiz Fusion and everything else needed, launch Compiz Fusion Icon (at Gnome it is located at Applications-->System Tools).
Tip: In order to launch Compiz Fusion during startup go to System-->Preferences-->Sessios and at the startup tab click new. At the name field add whatever you want (ex. Compiz Fusion Icon) and at the command field add fusion-icon
Tip: If your windows have no borders, right click at fusion-icon (at your system tray) and go to select window decorator and then select Emerald.
Created by ElemonGW. For more visit [http://elemongw.awardspace.com/](http://elemongw.awardspace.com/)
root@linuxhomepc:/home/don/Desktop#

Whenever it said:
(Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
I pressed enter and it asked again for each line until i hit enter and it finished...

---

### Post by upthelum on 2007-07-28
Oh btw this was a script i installed form [here]("http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz+fusion").

---

### Post by forestpixie on 2007-07-28
Sorry I have no idea - you might want to post this at the thread you got the script from.

When you got to this bit though - 

Whenever it said:
(Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
I pressed enter and it asked again for each line until i hit enter and it finished...

 - I think you could have closed the window to stop because you had errors.

Good luck with it :)

---

### Post by upthelum on 2007-07-28
Ok thanks anyway.

---

### Post by upthelum on 2007-08-03
Solved after an upgrade.

---


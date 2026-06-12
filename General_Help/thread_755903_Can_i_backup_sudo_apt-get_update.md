---
title: "Can i backup sudo apt-get update?"
date: 2008-04-15
forum: General Help
---

### Post by sjyoon on 2008-04-15
Can I backup sudo apt-get update?

when i installed programs,

I found *.deb files in /var/cache/apt/archives/*.deb

and /var/lib/apt/lists changed

when i command sudo apt-get update, what kind of file would changed?

if i backup apt-get update, I can install programs without internet connections


thanks in advance.

---

### Post by bradwilliamson on 2008-04-15
The command:
sudo apt-get update 

Updates the list of available software from the Internet or CD and modifies the pkgcache.bin and srcpkgcache.bin files.

Installing or upgrading software downloads the .deb package file and keeps a cached copy (for a while, depending on disk space, age, etc.) in /var/cache/apt/archives.

So, yes, if you installed, say, apache2 from the internet, then uninstalled it, you would be able to reinstall apache2 without needing an internet connection for the second install.

You can actually go to the /var/cache/apt/archives folder and install anything in there by hand with:
sudo dpkg -i zip_2.31-3_i386.deb

I use this for updating systems in a pinch where you can copy the archives directory over to a recently built machine, run apt-get update && apt-get upgrade and it will pull as much as it can from the archive directory, and download anything that changed between when the first system was updated and the second one was updated.

Probably not the officialway to do that, but it works for me.

Brad

---

### Post by sjyoon on 2008-04-15
thanks for the answer

when I command  sudo apt-get install mplayer

i got this message


before sudo apt-get update

////////////////////////////////////////////
sudo apt-get install mplayer

Reading package lists... Done
Building dependency tree... Done

E: Couldn't find package mplayer

////////////////////////////////////////////


after sudo apt-get update


///////////////////////////////////////////
sudo apt-get install mplayer

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  esound-common libartsc0 libaudio2 libdv4 libdvdread3 libesd-alsa0 libfaac0
  libggi2 libgii0 libgii0-target-x liblame0 liblircclient0 libmad0 libmp4v2-0
  libmpcdec3 libsdl1.2debian libsdl1.2debian-alsa libsmbclient libungif4g
  libxvidcore4 mplayer-skins
Suggested packages:
  nas libdvdcss2 esound libggi-target-emu libggi-target-monotext libggimisc2
  lirc w32codecs libdvdcss mplayer-doc
Recommended packages:
  libdv-bin esound-clients libggi-target-x libggi-target
The following NEW packages will be installed:
  esound-common libartsc0 libaudio2 libdv4 libdvdread3 libesd-alsa0 libfaac0
  libggi2 libgii0 libgii0-target-x liblame0 liblircclient0 libmad0 libmp4v2-0
  libmpcdec3 libsdl1.2debian libsdl1.2debian-alsa libsmbclient libungif4g
  libxvidcore4 mplayer mplayer-skins
0 upgraded, 22 newly installed, 0 to remove and 133 not upgraded.
Need to get 5765kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////


pkgcache.bin and srcpkgcache.bin 

/var/cache/apt/pkgcache.bin
/var/cache/apt/srcpkgcache.bin

/var/cache/apt/archives/*.deb
/var/lib/apt/lists/*

i backup bin,deb,gpg but not working 
in case..... sudo apt-get install programs

any ideas?

---

### Post by bradwilliamson on 2008-04-15
That behavior makes sense if you installed from a CD with limited packages and then enabled internet repositories and ran update, now you have many more packages available to you.

However, I guess I don't understand what you are trying to do.

Are you trying to download all packages and have them available offline? To do that will take a long time and many, many GB of disk.

Please explain what you are asking more clearly.

Thanks,
Brad

---

### Post by sjyoon on 2008-04-16
I have computer that can't connect internet

computer has modem port , not lan port

I can't command sudo apt-get update 

I know  "var/cache/apt/archives/*.deb" is program install files

if I can backup "apt-get update"`s  situation which file is changed

copy *.deb files and changed file from "apt-get update"

to new install ubuntu computer 

I can install programs without "apt-get update" and without internet connection

I can install program without dpkg -i command

I can use sudo apt-get install programs

like this
/////////////////////////////////////////
sudo apt-get install mplayer

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
esound-common libartsc0 libaudio2 libdv4 libdvdread3 libesd-alsa0 libfaac0
libggi2 libgii0 libgii0-target-x liblame0 liblircclient0 libmad0 libmp4v2-0
libmpcdec3 libsdl1.2debian libsdl1.2debian-alsa libsmbclient libungif4g
libxvidcore4 mplayer-skins
Suggested packages:
nas libdvdcss2 esound libggi-target-emu libggi-target-monotext libggimisc2
lirc w32codecs libdvdcss mplayer-doc
Recommended packages:
libdv-bin esound-clients libggi-target-x libggi-target
The following NEW packages will be installed:
esound-common libartsc0 libaudio2 libdv4 libdvdread3 libesd-alsa0 libfaac0
libggi2 libgii0 libgii0-target-x liblame0 liblircclient0 libmad0 libmp4v2-0
libmpcdec3 libsdl1.2debian libsdl1.2debian-alsa libsmbclient libungif4g
libxvidcore4 mplayer mplayer-skins
0 upgraded, 22 newly installed, 0 to remove and 133 not upgraded.
Need to get 5765kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 

//////////////////////////////////////

sorry my poor explanations..

---

### Post by gsmanners on 2008-04-16
If you have a computer that is not connected to the internet, the easiest way to handle that is by making your own disc with files that you want (assuming you have a CD/DVD drive on the disconnected computer).

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by sjyoon on 2008-04-16
thank you...gsmanners

aptoncd is what i want...

I use dapper 6.06 


I can't install APTonCD my dapper 6.06

when i command "sudo apt-get install aptoncd"

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package aptoncd

and 

use package installer and "dpkg" command

to "aptoncd_0.1-1_all.deb" file

sudo dpkg -i aptoncd_0.1-1_all.deb


Selecting previously deselected package aptoncd.
(Reading database ... 54710 files and directories currently installed.)
Unpacking aptoncd (from aptoncd_0.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of aptoncd:
 aptoncd depends on python-support (>= 0.2); however:
  Package python-support is not installed.
 aptoncd depends on libgnomevfs2-0; however:
  Package libgnomevfs2-0 is not installed.
 aptoncd depends on yelp; however:
  Package yelp is not installed.
 aptoncd depends on nautilus-cd-burner; however:
  Package nautilus-cd-burner is not installed.
 aptoncd depends on python-gnome2; however:
  Package python-gnome2 is not installed.
 aptoncd depends on python-dbus | python2.4-dbus; however:
  Package python-dbus is not installed.
  Package python2.4-dbus is not installed.
dpkg: error processing aptoncd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 aptoncd

I can't install APTonCD

---

### Post by gsmanners on 2008-04-16
No, I think APTonCD requires Feisty (7.04) or newer.

---


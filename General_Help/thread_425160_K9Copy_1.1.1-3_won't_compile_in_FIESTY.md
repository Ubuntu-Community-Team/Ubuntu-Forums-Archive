---
title: "K9Copy 1.1.1-3 won't compile in FIESTY"
date: 2007-04-27
forum: General Help
---

### Post by paulstaf on 2007-04-27
I am going nuts with this!

I use K9Copy to backup my kids dvds and keep the originals safe.  Crazy little monkeys eat dvds for breakfast!

Anyway, I had to go to Fiesty because I couldn't get my new monitor to go into 1600 x 1200 mode with Edgy.  Now the monitor works fine....BUT

The version of K9copy that comes out of the repository: 1.1.0, doesnt' seem to be working right...it keeps creating 7 gig ISO files instead of compressing it down to 4.7GB even though I have in the settings as a 4.4 gig file.

So I figured I would install the latest version 1.1.1-3.  I downloaded it and tried to ./configure and I get this error first:

[B]checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss[/B]

I have installed every package I can think of regarding that and yet it still doesn't go past this.
So I went in the ./configure file and bypassed the check for this and now it goes past, but then stops with this QT error:

[B]checking for Qt... configure: error: Qt (>= Qt 3.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support![/B]

The last lines of the config.log file are:

[B]#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_DLFCN_H 1

configure: exit 1
[/B]

I have installed just about every QT thing I can find.  I admit, I have only been using Linux for 6 months, but I have learned pretty quickly and still cannot figure this one out. 

I cannot find any information out there that has resolved this.

Thanks in advance...

---

### Post by rbmorse on 2007-04-27
have you installed build-essential?

---

### Post by kpkeerthi on 2007-04-27
Open synaptic and search for "qt mt" (without quotes) and install the dev package. 

PS: I installed all dev packages and ./configure was successful. However, make fails. Do let me know how it goes for you.

---

### Post by paulstaf on 2007-04-27
Yes on the build essentials.

Already installed all the qt packages including the dev.

Still won't make it past there.

This is Fiesty.

The real problem is that I cannot get the K9copy I have to create an ISO image less than 7.4 gigs.

It is like it isn't shrinking.  

I have tried every setting in there.

Think this new version might work, but you would think even the one in the repositories would work....

Thanks...

---

### Post by kpkeerthi on 2007-04-28
Check this out [http://ubuntuforums.org/showthread.php?t=425802](http://ubuntuforums.org/showthread.php?t=425802)

---

### Post by paulstaf on 2007-04-28
Well, I finally gave up.  During the course of trying to uninstall one libdbus and install another, I hosed my gnome.  Could have probably fixed it, but just reloaded it from scratch.  FIrst thing I did was run the commands below and then did the configure and the make and it worked fine.  I got that from this thread:  [http://ubuntuforums.org/showthread.php?t=425802](http://ubuntuforums.org/showthread.php?t=425802)  but for some reason I can never get stuff all on one line to install...so I broke it out into a script like this:

sudo aptitude install dvdauthor
sudo aptitude install libdvdread3 
sudo aptitude install mencoder 
sudo aptitude install mplayer 
sudo aptitude install libhal1
sudo aptitude install libdbus0 
sudo aptitude install libdbus-qt-1-1
sudo aptitude install libdvdread3-dev 
sudo aptitude install libqt3-headers 
sudo aptitude install libqt3-mt-dev 
sudo aptitude install kdebase-dev 
sudo aptitude install kdelibs4-dev 
sudo aptitude install libqt3-mt-dev 
sudo aptitude install qt3-dev-tools 
sudo aptitude install libqt3-headers 
sudo aptitude install libjpeg62-dev 
sudo aptitude install build-essential 
sudo aptitude install checkinstall 
sudo aptitude install libhal-dev 
sudo aptitude install libdbus-qt-1-dev 
sudo aptitude install libhal-storage-dev

Anyway, after the new install and this script, it worked fine.

Thanks for the help....

---


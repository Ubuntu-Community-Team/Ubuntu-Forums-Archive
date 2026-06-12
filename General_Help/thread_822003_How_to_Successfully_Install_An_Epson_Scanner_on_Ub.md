---
title: "How to Successfully Install An Epson Scanner on Ubuntu"
date: 2008-06-07
forum: General Help
---

### Post by kureyamu on 2008-06-07
These instructions are for a Perfection 1650 or Epson GT-8200 Scanner on Ubuntu Hardy Heron, but may well help users install other scanners.

The installation and use of a scanner comes in two parts:

(1) make sure all necessary dependencies are installed and check that you can use the scanner as root;

(2) add root and your name (and other user names if your system is shared) to the scanner user group.

----------------------------------------

So re part (1): do the following:

(a) go to System/Administration/Synaptic Packet Manager and make sure the following packets are installed; if you add any, reboot after their installation:

libsane 1.0.19-1 ubuntu 3
libsane-extras 1.0.18.12 ubuntu 1
sane-utils 1.0.19-1 ubuntu 3
xsane 0,995-1 ubuntu 1
xsane-common 0.995-1 ubuntu 1
xsane-doc 0.995-1 ubuntu 1
libusb-0.1.14 2:0.1.12-8

lprof (version 1.11.4.dfsg+1.11.4.1-3) and its dependencies, as detailed below (LibProf is used if you need to set up a Colour Profile for CMS, the Colour Management System - i installed LibProf but did not need to use it):libprof dependencies: 
libfftw3-3 (version 3.1.2-3ubuntu1)
libvigraimpex2 (version 1.5.0-1ubuntu2)
qt3-assistant (version 3:3.3.8-b-0ubuntu3) 
qt3-doc (version 3:3.3.8-b-0ubuntu3)

(b) make sure that kooka or other scanner software that may cause conflict is not installed.

(c) plug in your scanner and click on Applications/Graphics/XSane Image Scanner ... you will probably get a message that no scanner can be found; this action was included just in case a miracle happened.

(d) open a terminal, become root and nudge your system into wakefulness with the command line:

sudo updatedb  (press Enter and give your password)

(e) run the scanner as root with the command line:

sudo /usr/bin/xsane 	(you will get warning messages but ignore them and press Enter)

(f) if the scanner works fine as it should, go to part (2) setting user permissions

--------------------------------------------

So re part (2): do the following:


(a) go to System/Administration/Users and Groups and give your password to authenticate.

(b) there are 2 categories: (1) name: "your user name" eg. keith (2) name: "root". 

(c) highlight "root" and click on "Manage Groups" to open a list which includes "scanner."

(d) click on Properties and it should show 2 Group Members: you and root: the boxes will be unchecked so tick them and close the dialog box.
if, as in debian etch, the names are not there, then add them.

(e) reboot and plug in the scanner. it should work fine. if you have problems, you may have to use LProf to make a Colour Profile.
my own scanner works to perfection after having installed it as above. best wishes, kureyamu

----------------------------------------------

*[CENTER]microsoft was a 20th century operating system[/CENTER]*

---

### Post by Hollihock on 2008-08-12
It worked!!!  Thank you so much!  I followed part 1 of your instructions, through "c", and I got that miracle you mentioned.  The scanner was recognized and actually worked!  I had just gotten the printer to work, assisted by another thread.:)
  By the way... I am talking about an **Epson Stylus CX8400** "All-in-One".  Got the printer working by calling it a CX7800.  I was on the verge of putting the whole thing out for the trash man.  The color on the printer is really close to the screen... and the scanner works great with all the options available too!
   I hope this helps someone else with similar problems.
 Thank you again, very much!

Forgot... Hardy, dual booting with XP, on an Acer desktop with Core 2 Duo.

---

### Post by rowland on 2011-03-11
> **kureyamu said:**
> 

(b) there are 2 categories: (1) name: "your user name" eg. keith (2) name: "root". 

(c) highlight "root" and click on "Manage Groups" to open a list which includes "scanner."

(d) click on Properties and it should show 2 Group Members: you and root: the boxes will be unchecked so tick them and close the dialog box.
if, as in debian etch, the names are not there, then add them.

(e) reboot and plug in the scanner. it should work fine. if you have problems, you may have to use LProf to make a Colour Profile.
my own scanner works to perfection after having installed it as above. best wishes, kureyamu

----------------------------------------------

*[CENTER]microsoft was a 20th century operating system[/CENTER]*

highlighted root, clicked on manage group, there is a list, but there isnt anything named scanner there...
(Ubuntu 9.10 karmic, 2.6.31-22-generic) & Epson Stylus SX-205

---

### Post by bluexrider on 2011-11-22
I don't have an issue with the Printer. 

I have an issue finding out what the ink levels are?

Can someone help??

---


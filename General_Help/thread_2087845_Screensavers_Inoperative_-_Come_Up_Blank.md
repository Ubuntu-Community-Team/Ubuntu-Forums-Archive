---
title: "Screensavers Inoperative - Come Up Blank"
date: 2012-11-24
forum: General Help
---

### Post by Johnny M! on 2012-11-24
_24-Nov-2012_
[COLOR=Purple]**Have Screen-Saver Problem**[/COLOR] 

Hi All,

Ubuntu 10.04 Linux Kernel = 2.6.32-45

Within the last week or two, many of my installed screensavers quit working.  They show up in System - Preferences - Screensaver; but when commanded to Preview - they just show a blank screen.    And when they activate on my monitor screen (after 5 minutes of Idle) they show nothing but a Blank Screen.

I've been using rss-glx (Really Slick Screensaver's) 'Skyrocket' for years without Problem.   Now, not only does 'Skyrocket' go Blank, all other rss-glx screensavers are blank also.   As do many others - I'd say half my 200 screensavers exhibit this Blank (Bad) Behaviour.

I've uninstalled and reinstalled the screensavers in Package Manager (and once in Terminal) multiple times and have had no luck getting my 'Skyrocket' screensaver functional.   Used terminal Command:
sudo apt-get install  rss-glx  xscreensaver-gl-extra  xscreensaver-data-extra

Since the end of September I've updated the Linux Kernel 3 times ( 2.6.32-43 / 44 / 45).  
I've rolled back and booted with 2.6.32-43 (when it worked) with no success.   I've made No Hardware and/or Driver changes withing the time period from the screensavers were working to when they are NOT working (now).

Any Ideas - Any Help = will be most appreciated !
THANX in Advance.

BVR
Johnny M!


PS: Just installed 'rss-glx' in Linux Mint 13 Maya and "Skyrocket' screensaver worked perfectly !   Why not working in Ubuntu ?????

---

### Post by Johnny M! on 2012-11-25
_Screensaver Inventory:_

My 'Skyrocket' Screensaver has worked for years with no Problems. 

Then my[COLOR=Purple]** 'Skyrocket'**[/COLOR] screensaver by rss-glx  Screen Savers (Really Slick Screensavers collection by Terry Welsh  ([http://www.reallyslick.com/](http://www.reallyslick.com/))) went inoperative just within the last week or  two - I just noticed it wasn't working the day after this Thanksgiving.     

I uninstalled and reinstalled rss-glx in Package Manager to no avail.

Then, after running the following Terminal Command:
**[COLOR=Purple]sudo apt-get install  rss-glx  xscreensaver-gl-extra  xscreensaver-data-extra[/COLOR]**

I now have (in addition to Blank Screen and Random) 240 Screen Savers listed in System - Preferences - Screensaver

Of those 240 listed; only about half (117) actually Preview and work.   The 123 that don't work just display a Bank Screen.   Wondering Why ??????

Any suggestions much appreciated  - THANX in Advance !

BVR
Johnny M!

---

### Post by Johnny M! on 2012-11-26
_Monday 26-Nov-2012_

PROBLEM Solved - a simple back to basics Fix:

Apparently, the multiple Linux Kernel upgrades (43-44-45) affected some Graphic configuration settings (fglrx in Jockey's Hardware Drivers versus the direct install from AMD Driver Downloads) .   

I updated my AMD Graphics Driver IAW the following instructions:
[INDENT]Install ATI Drivers - Ubuntu 10.10 & 12.04 
[http://www.youtube.com/watch?v=eS9Nmet_sqQ](http://www.youtube.com/watch?v=eS9Nmet_sqQ)
[/INDENT]I installed AMD CCC 12.10; and now this Terminal Command: "ls /var/lib/dkms/fglrx/" shows 
AMD CCC 12.10   AMD Display Driver 9.002

[SIZE=4]And [COLOR=Purple]**voilà**[/COLOR] - my [COLOR=Blue]**'Skyrocket**[/COLOR]' Screensaver Works ![/SIZE]

---


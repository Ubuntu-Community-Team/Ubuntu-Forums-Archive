---
title: "Monitor drivers"
date: 2007-02-21
forum: General Help
---

### Post by warlock_handler on 2007-02-21
Hi guys,
I have recently installed uBuntu, I am using a 19" wide screen monitor and it has specific display drivers to it, found on:
[http://www.samsung.com/support/productsupport/download/Model_Select2.aspx?type=Monitor&subtype=LCD+%2D+Digital&model=940BW&fileType=DR&LSSI=%2Finclude%2FSSI%2Fus%5Fleft%2FLMenu%5FMonitor%5FLCD%5FDigital%2Esec&RSSI=%2Finclude%2FSSI%2Fus%5Fright%2FRMenu%5FMonitor%2Esec](http://www.samsung.com/support/productsupport/download/Model_Select2.aspx?type=Monitor&subtype=LCD+%2D+Digital&model=940BW&fileType=DR&LSSI=%2Finclude%2FSSI%2Fus%5Fleft%2FLMenu%5FMonitor%5FLCD%5FDigital%2Esec&RSSI=%2Finclude%2FSSI%2Fus%5Fright%2FRMenu%5FMonitor%2Esec)

however that is a windows executible, so i was wondering as to how I would install this in uBuntu.... 

also i read somewhere that i can use Wine to execute windows executables on ubuntu and I downloaded it frmo here:
[http://wine.budgetdedicated.com/archive/ubuntu/breezy/wine_0.9.19~winehq0~ubuntu~5.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/breezy/wine_0.9.19~winehq0~ubuntu~5.10-1_i386.deb)

but how do i install it, i dont know how to install it, please help me on this...

---

### Post by luisromangz on 2007-02-21
Well you shouldn't try to install these drivers with Wine, as Wine is not designed to be able to allow the use of Windows drivers as Linux kernel modules.

You shouldn't worry, as drivers for monitors in Windows only use is to customize the control panel dialog (as far as I remember from my Windows days).

So, if your monitor works, you don't need these drivers.

---

### Post by Spr0k3t on 2007-02-21
Monitor drivers are not needed.  You really only need the horizontal and vertical refresh information and be done with it.

---

### Post by warlock_handler on 2007-02-21
> **luisromangz said:**
> Well you shouldn't try to install these drivers with Wine, as Wine is not designed to be able to allow the use of Windows drivers as Linux kernel modules.

You shouldn't worry, as drivers for monitors in Windows only use is to customize the control panel dialog (as far as I remember from my Windows days).

So, if your monitor works, you don't need these drivers.

ok thats a cool tip.. 

yes my monitor is working fine... so i guess i will simply ignore the monitor drivers...

also can u help me with my doubt on Firefox... do i overwrite the old version with the new tar that i downloaded???

or do i unzip it in another location and run it from there?...

---

### Post by warlock_handler on 2007-02-21
> **Spr0k3t said:**
> Monitor drivers are not needed.  You really only need the horizontal and vertical refresh information and be done with it.

ok how do i edit the default vertical and horizontal locations???

(ps. i am new to linux, sorry if these questions are too dumb)

---

### Post by Spr0k3t on 2007-02-21
> **warlock_handler said:**
> ok how do i edit the default vertical and horizontal locations???

There is a way to do this, however if you are new to linux you really should not be modifying this part.  Get to know linux a bit more and then start tweaking your /etc/X11/xorg.conf file.  Bear in mind, changing almost any aspect of this one file will prevent X11 from running.  If your system is running at the optimum resolution you are wanting, I would leave it.

Edit:  Let me qualify this with a bit of personal experience.  When I started poking around trying to tweak my display settings, I dove deep into xorg.conf and didn't bother to make a backup.  I'm not exactly a linux newb, this is just my first time through since going back to WFWG 3.11 (windows for workgroups).  Back then X was on the horizon.  So I made a major blunder and ended up reinstalling from scratch.  Later when I fealt a bit more comfortable and researched on how I needed to change my settings, i went back into xorg.conf and was able to edit the file with no problems, I even setup twinview and custom screen sizes while I was at it, and now all my mouse buttons work as well (Logitech MX518 ).  I think without the information I learned by researching deep about xorg.conf, I don't think I would have stuck around and gone back to my dreary ways of windows usage.

---


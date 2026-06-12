---
title: "OpenOffice.org apps won't start"
date: 2007-10-10
forum: General Help
---

### Post by j3ff on 2007-10-10
Hi,
I am using the x64 version of the Gutsy Gibbon beta release.  I have installed all updates.

My problem is that none of the openoffice apps will start.  I see the spash screen briefly
and then nothing.  System monitor shows nothing out of the ordinary.  No ongoing CPU or
mem consumption.  No openoffice processes remaining.

I have done various searches through the forums but many of the posters experienced different symptoms.  I am yet to discover the solution, or even whether there is one currently.

I haven't done anything wierd like install automatix.  I've install various packages from the repositories, and I'e installed all updates.

I'm not sure whether OOo worked immediately after installing the OS as I don't think I tried it.  

In summary:  I've installed and updated the x64 edition of Ubuntu 7.10 beta.  I've never seen openoffice apps work.  All I get is the splash screen briefly.

My PC:  Asus P5K (intel P35), 
           Intel E6750 (core 2 duo), 
           1GB DDR2 800MHz, 
           Nvidia Geforce 8500GT
           Seagate 250GB HDD 

Has anyone else experienced this?
Can someone please point me to a solution (assuming that there is one)?
Or can I expect that an update will fix this problem for me in due course?

Any help, info or advice will be greatly appreciated.

Thanks,
Jeff

---

### Post by dpar on 2007-10-10
Do you get any errors if you start it in terminal??

> ooffice -writer %U

---

### Post by j3ff on 2007-10-10
> **dpar said:**
> Do you get any errors if you start it in terminal??

Yep.

> Jeff@jeff:~$ ooffice -writer %U

** (process:6572): WARNING **: Unknown error forking main binary / abnormal early exit ...
jeff@jeff:~$ ooffice -writer

** (process:6593): WARNING **: Unknown error forking main binary / abnormal early exit ...




---

### Post by j3ff on 2007-10-11
OK, openoffice seems to be working now.  Here's what I did:-

(1) ctrl-alt-backspace to restart X and GDM.  Then tried running Writer before doing anything else.  This didn't help me at all.  Writer still would not start.

(2) Using synaptic I **_reinstalled_** the following: openoffice.org, openoffice-core, openoffice-gnome, openoffice-gtk, openoffice-base, openoffice-calc, openoffice-draw, openoffice-writer, openoffice-impress, openoffice-common.  

After (2) I have been able to run the openoffice apps.  

It seems that this problem has been occurring for some users since fiesty, maybe even Edgy.  I was including the gutsy in my searches.

To anyone seeking a solution to this problem, I can only suggest that you try reinstalling
the openoffice packages.  That's what worked for me.

Cheers,
Jeff

---

### Post by Lucho77 on 2007-10-22
> **dpar said:**
> Do you get any errors if you start it in terminal??

I did run it without the last part, and worked, like this;
$ooffice -writer

Thanks 'dpar'

---


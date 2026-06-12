---
title: "Making a read-only bootable USB for Ubuntu"
date: 2012-10-23
forum: General Help
---

### Post by BrianTWhite on 2012-10-23
Hi all
I'm not sure which part of ubuntu to post this to, but I thought I'd try with this one.
I teach a big freshman bio class and administer about 30 mac computers in a teaching lab. Mac os is getting harder to administer every day.

I need to be able to add some custom applications and a desktop and the students need to be able to save things temporarily (for one 3-hour lab session only), but once they log out, I want to completely wipe any things they've saved as well as any customizations they've changed.

In the past, I've used live linux cds (I made a custom version of knoppix) with PC hardware. Unfortunately, some of my macs don't have cd-drives. So I'd like to make a bootable version of ubuntu that I can customize that will run off of a USB drive but not be modifiable by the user (like the cd was).

I've tried googling this but I get hits like this: [http://ubuntuforums.org/showthread.php?t=1881701](http://ubuntuforums.org/showthread.php?t=1881701)
which look like a situation where being read only is BAD and needs to be fixed - so I'm nervous about looking into them.

Do you have any suggestions?

Thanks for your time.

Brian

---

### Post by Kidwell on 2012-10-23
UNETBOOTIN will do what you want.  Search for it on Google. It makes USB drives into bootable ISO's.  I keep one around with a version of puppy linux, and ubuntu 12.04 desktop live.  Does exactly what your talking about.

Another good one for multiple live OS's is YUMI.  However I've only ever been able to get YUMI to work properly in a Windoze environment.  Please post back with your results! Always interesting to hear of how people implement Linux distros.

---

### Post by BrianTWhite on 2012-10-23
That looks perfect!
I will look into it and get back to you (it may take a little time....)
Thanks!

Brian

---

### Post by C.S.Cameron on 2012-10-23
Welcome to the forums.

Both UNetbootin and Startup Disk Creator, (from the live cd), will make persistent installs.

A persistent install saves data in a file named casper-rw, This might be useful in case of power failure or whatever. 
The casper-rw file can be replaced after each session.

If loosing data halfway through a session is no big deal, then a non persistent install is good enough.

A 1 GB pendrive is probably large enough for your requirements, the basic install, (no persistence), takes 800MB.
You can make a custom iso for installing to external drive using remastersys.

---

### Post by BrianTWhite on 2012-10-24
Hi folks
    Sorry if I'm being dense, but I looked at the site for UNETBOOTIN and while it clearly allows making a bootable USB, there are two parts that I'm not clear on. I'm not familiar with the terminology, but I don't see how to do two other parts of my task:

1) Customizing the ubuntu myself and then making an iso image of that (adding apps & setting up the desktop, prefs, etc.). I can handle the customization - I'm just not sure how to make an .iso of an existing customized linux setup.

2) Make the bootable USB read-only. That way, the users can't leave/change anything permanently on the machine.

   Did I miss something when I looked at the UNETBOOTIN site?

   Thanks again for your time!

Brian

---

### Post by C.S.Cameron on 2012-10-24
1) Remastersys

2) Install to USB using UNetbootin or Startup Disk Creator without using the persistence option.

---

### Post by since on 2012-10-24
try


```
dd
```

stands for disk dump

and dump your iso to the stick

---

### Post by C.S.Cameron on 2012-10-24
Be extremely cautious using dd, you can overwrite everything, including your internal drive.
There is no undo with dd.

---


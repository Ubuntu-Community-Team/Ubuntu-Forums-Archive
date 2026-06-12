---
title: "Ubuntu error hal.dll"
date: 2008-03-24
forum: General Help
---

### Post by abraze on 2008-03-24
I looked at a couple of other topics before deciding that my problem seemed unique enough to warrant a topic, but just in case there is one, please point it out.

I installed ubuntu using wubi because my laptop doesnt have a disk drive, first off lets get back to the reason I even installed it, it was because windows just wasnt working, it was such a pain to even get wubi working that I treated it as a godsent when it actually worked.

Anyways, ubuntu loaded up fine the first time, but after an hour or so, my computer mysteriously turned off, when I tried turning it back on, everything went fine right until it asked me whether I wanted to run xp or ubuntu, so then after I clicked on ubuntu it spent a couple of minutes thinking it over before it finally told me that there the hal.dll file was missing, and that I should reinstall windows or something. I thought this was kind of strange because I wasnt trying to open windows.

So now, I'm locked out of ubuntu because everytime I try and boot from it, it gives me the hal.dll statement, but the funny thing is, I can load into windows just fine. Isnt it a windows directory? shouldnt windows crash? If someone could just explain to me why this happened and how I can fix it.
Thanks a bunch
-Abraze

---

### Post by abraze on 2008-03-24
wrong thread I think. I'll delete it. sorry.

---

### Post by Sef on 2008-03-24
Moved to the Wubi forum.

---

### Post by ago on 2008-03-24
What wubi version was that?
Also see: [https://bugs.launchpad.net/wubi/+bug/133603](https://bugs.launchpad.net/wubi/+bug/133603)

---

### Post by Mortel on 2008-03-24
> **ago said:**
> What wubi version was that?
Also see: [https://bugs.launchpad.net/wubi/+bug/133603](https://bugs.launchpad.net/wubi/+bug/133603)

I JUST recovered from the same problem as you, does it say that the hal.dll file is corrupted or missing?  It shouldn't let you boot into windows either, giving the same message.

What i did was:

Get the Windows XP CD, doesn't matter if it's one to upgrade, or to install Windows, any of them work I think.

Let it start the setup process.  Then, when it gives you the option, press "R" to go into the recovery console.

once in, it asks you to select which windows installation you want to go into.  Just type "1" and hit enter.
For me, I just hit enter for the admin password, but if you have one, type it in and press enter.

You should now be in the C:\WINDOWS directory.  If not, navigate there I guess, although you should be there by default.
Next, type in the following command:
```
expand d:\i386\hal.dl_
```
(Replace D with the letter assigned to the CD drive that the Windows CD is in)
If it gives you an option to overwrite the file, type "Y" and hit enter.  If it doesn't, type in the command again, and it should ask you if you want to overwrite it.
Finally, type "exit", and your PC should reboot normally.  =D

That is the fix if the problem is actually the hal.dll file, it might also be the boot.ini file.

---

### Post by abraze on 2008-03-24
I'm running wubi 7.04, and part of my problem was that I dont have a disk drive at all, so I probably need another way to fix it than that. I tried replacing the hal.dll straight into the c drive by downloading it from somewhere online, that didnt work. So what would be a solution? Should I get a portable disk drive? Or is there 'through windows' way to clean up the mess?

---

### Post by ago on 2008-03-24
Ignore my bug report above misread hald/hal.dll...

You can try to run chkdsk /r from the recovery console.
There are some rc iso disks available for download.

---

### Post by Termy58 on 2008-03-26
Possible fix? 
[http://shanegfowler.wordpress.com/2007/01/10/missing-haldll-error-corrupt-bootini-file-quick-fix/](http://shanegfowler.wordpress.com/2007/01/10/missing-haldll-error-corrupt-bootini-file-quick-fix/)

---

### Post by ago on 2008-03-26
Try to uninstall, make sure there is not wubildr* or grldr* or menu.lst in C:\

then run wubi 8.04

---


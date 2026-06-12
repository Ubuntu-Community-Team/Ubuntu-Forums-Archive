---
title: "No Ubuntu on computer start-up running Windows 7"
date: 2013-12-29
forum: General Help
---

### Post by dscott48 on 2013-12-29
I have been running Ubuntu and Windows 7 for a couple years.  I have a choice when I start the computer.  Recently that choice disappeared and it now only goes to Windows.  At first it offered the choice but wouldn't open Ubuntu, then I ran boot-repair and that option disappeared completely.  I am still showing 144Gb of Ubuntu in drive C  and all the start up applications appear to be there.  The first time I ran boot-repair it removed all of Grub.  I have since run it in Ubuntu with the live cd, try me, using the terminal to download and run.  I am at a loss,  have been working on it for three days 12 to 16 hrs a day and I am no better off.

---

### Post by Impavidus on 2013-12-30
> **dscott48 said:**
> I have been running Ubuntu and Windows 7 for a couple years.  I have a choice when I start the computer.  Recently that choice disappeared and it now only goes to Windows.  At first it offered the choice but wouldn't open Ubuntu, then I ran boot-repair and that option disappeared completely.Sounds like you lost your kernel. Without kernel Ubuntu cannot boot. Boot-Repair detected no kernel and therefore removed the entry for Ubuntu from the menu.> I am still showing 144Gb of Ubuntu in drive C  ...Meaning ...? Drive C is your Windows partition. Ubuntu cannot exist in your Windows partition, unless it's wubi, but that cannot be 144GB.> ... and all the start up applications appear to be there. What do you mean by that?> The first time I ran boot-repair it removed all of Grub.  I have since run it in Ubuntu with the live cd, try me, using the terminal to download and run.Could you post a link to the boot info summary?> I am at a loss,  have been working on it for three days 12 to 16 hrs a day and I am no better off.Don't work on a problem 16 hours a day. It cuts into your sleep, which can improve your productivity for at most three days. Don't listen to the "work hard, sleep when you're dead"-gurus. They're wrong.

---

### Post by Mark Phelps on 2013-12-30
If you had a Wubi install and you did some Windows updates, it's possible the one of them reset the BCD to remove the Ubuntu entry.  Since WUBI does not use GRUB, installing GRUB only made matters worse.

To see what you have, boot back into Windows and look for a file on the "C:" drived named root.disk.  IF that file is there, you have a WUBI installation.

---

### Post by dscott48 on 2013-12-30
I do have a Wubi installation.  
I did do some windows updates, the one thing I dislike about windows.  I have updates shut off, yet it updates anyway.
I would love to remove windows and only use ubuntu, but that are some things I haven't learned to be able to do in Ubuntu as well as windows.
At first in rebooting, I would get the choice to go into either os, then after running boot-repair, that completely disappeared and it goes straight to windows.
I downloaded a copy of Ubuntu on cd and have been trying to run the terminal to fix from there.

---

### Post by grahammechanical on 2013-12-30
Can you not re-install Ubuntu using wubi.exe in the same way that you installed it in the first place? You may need to remove Ubuntu using some Windows utility (Add/Remove programs? does Windows still use that?) and then install.

Regards.

---

### Post by dscott48 on 2013-12-30
I was afraid if I re-install Ubuntu, I wll lose all my documents and everything I have added since having it.

I have now been trying to run the boot info script in terminal, but the commands on the wubi thread aren't working.

---

### Post by dscott48 on 2013-12-30
The first solution to my problem of being able to load windows and not Ubuntu, means running the boot info script.  I can download it and move the tar to my documents, but the terminal won't accept the commands that are listed in the wubi thread for getting this infomation.  Everything seems to fall back on having this info and I can't get it.

---

### Post by Mark Phelps on 2013-12-30
Don't use WUBI myself -- as it's NOT intended for long-term use and has a history of not surviving major version updates well.  Also, it's not supported anymore and has been discontinued.

I've heard that what might work is the following:
1) Boot into Windows
2) Attach an external drive and copy root.disk to that drive
3) Remove Ubuntu from Windows using the normal app removal sequence
4) Reinstall Ubuntu inside Windows using WUBI
5) Copy the saved root.disk over the recently installed root.disk
6) Reboot

---

### Post by dscott48 on 2013-12-30
If I do this, will it keep everything I have saved in Ubuntu, or do I loose it.

---

### Post by dscott48 on 2013-12-30
Running windows 7 under computer/C/Ubuntu/install/boot, there are no files, it is empty.  I am not sure if this should be, I have files from Sept. on my external hard drive and am trying to copy them back to their original location.  I don't know what these files are or if I should have them.  There must be lots of files there because it is taking a long time to copy them.  I have tried many things and nothing else seems to work, can't seem to get any answers to my questions.

---

### Post by dscott48 on 2013-12-30
I guess i am done.  Can't get any answers, everything I try seems to make it worse.  Trying to load Ubuntu files to external hard drive and the entire computer freezes at 62%, have tried three times.  Managed to start in safe mode to rename Ubuntu file and hopefully save it so I can reload a new Ubuntu.  From the Ubuntu disk I get as far as the partioning and nothing I try works.  Keeps saying I have to do something with the root file.  No matter what I choose it won't continue.  So I guess I am going to suck it up and completely delete Ubuntu and lose everything I have put there for more than two years.  Guess I should have known better.  Since I can't get any answers on here there is no sense in keeping it.  I will just go back to windows now for good.

---

### Post by hakuna_matata on 2013-12-31
> Running windows 7 under computer/C/Ubuntu/install/boot, there are no  files, it is empty.  I am not sure if this should be, I have files from  Sept. on my external hard drive and am trying to copy them back to their  original location.  I don't know what these files are or if I should  have them.
Files under **computer/C/Ubuntu/install/boot** are only used during installation process of Wubi. 

In your case the files under** computer/C/Ubuntu/winboot **are necessary to boot especially **wubildr.mbr**, **wubildr** and **wubildr.cfg** and a menu entry in Windows boot manager which calls **wubildr.mbr**

If  it is impossible for you to reinstall Wubi because you cannot back up  your root.disk, there is the possibility to create a menu entry with  EasyBCD: 

homepage of EasyBCD: [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

picture of a working menu entry for Wubi (entry #2): [http://media.cdn.ubuntu-de.org/wiki/attachments/01/45/EasyBCD-Setting.png](http://media.cdn.ubuntu-de.org/wiki/attachments/01/45/EasyBCD-Setting.png)

Dont' forget to set a timeout to display Windows 7 menu.

But if this happens under Windows 7:
> Trying to load Ubuntu files to external hard drive and the entire computer freezes at 62%, have tried three times.
you have Windows problems, 

Maybe Windows file system is corrupted. Try to check disk under Windows to fix system errors.

---


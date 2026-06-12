---
title: "Grub Stage 1.5 Message followed by a blank screen and a restart..."
date: 2007-12-07
forum: General Help
---

### Post by Nick11 on 2007-12-07
I checked the above threads and searched this topic, and I did not find any topics that are related to my exact problem. So, here it goes...

I have an HP laptop with Vista Home premium. Using Vista's partitioner I made a 10GB volume for Ubuntu, and a 2GB volume for the swap. Upon installation I selected "manual," and used the 10GB partition as the ext3 main directory using the "/." Then, I selected the 2GB volume as the swap, and I proceeded to install the OS. After, I see the dual boot menu with the options for Vista and Ubuntu and everything  seems to work fine.

Now, the problem is that after I select Vista, and boot into it a few times, I then get this error- what happens is that I start my computer, and a message that says "Grub  loading Stage 1.5..." comes up, and then it shuts down and restarts my computer. I cannot even get into the dual boot menu or go into Vista or Ubuntu any more. Thus, I am forced to reinstall the OS, loose everything I have done in Ubuntu, and start all over. 

I believe Vista may be overwriting the partition or is causing some conflict with the new volumes. I really need your help. I do not want to have to keep installing the OS as a result of this issue. I really like Ubuntu and I am just starting to fiddle around with things. Thanks in advance.

---

### Post by derby007 on 2007-12-07
Try the GParted live cd : [http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")
or the Vista CD, & choose the repair option, i think this fixes the MBR.

---

### Post by ronmarley1 on 2007-12-07
I had the exact same problem.  It may be a Vista issue, but I'm running XP, so my guess would be that it's not.  I think the cause of my problem was TrendMicro antivirus on XP seeing GRUB and trying to remove it from the MBR.  
As the above poster suggested, the SuperGRUB Disk will fix GRUB, until you boot into Windows again.
The solution for me was to use the Windows boot loader to select either Windows or Linux.  Selecting Linux goes to GRUB, then into Linux.
This is all explained at the following link:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by Nick11 on 2007-12-07
Thanks so much for the help. I will definitely try out your suggestions.

---

### Post by Nick11 on 2007-12-07
Hey guys, I managed to get something accomplished. You see Vista is not like XP in terms of booting. You have to access something called BCDEDIT though the command window. Instead of doing that I used this program call "Easy BCD." There is no boot.ini file to edit, as the article above mentions. So, I selected my partition that has Ubuntu using EasyBCD and rebooted.

Now, here is the problem. I still get the GRUB dual boot screen, and after I make a selection, _then_ the windows dual boot selection comes up. So, how do I get ride of the GRUB dual boot menu from handling my choices, so that the windows menu _only_ handles my options? Any help would be greatly appreciated, and thanks in advance.

---

### Post by ronmarley1 on 2007-12-08
> **Nick11 said:**
> Hey guys, I managed to get something accomplished. You see Vista is not like XP in terms of booting. You have to access something called BCDEDIT though the command window. Instead of doing that I used this program call "Easy BCD." There is no boot.ini file to edit, as the article above mentions. So, I selected my partition that has Ubuntu using EasyBCD and rebooted.

Now, here is the problem. I still get the GRUB dual boot screen, and after I make a selection, _then_ the windows dual boot selection comes up. So, how do I get ride of the GRUB dual boot menu from handling my choices, so that the windows menu _only_ handles my options? Any help would be greatly appreciated, and thanks in advance.

Thanks for the info.  I have no experience with Vista, except to set up my sister's wireless laptop.  I did not know that Micro$oft changed the was Vista boots.  
Unfortunately, I'm not able to help you with your issue.  Hopefully someone with Vista experience will help.
Good luck!

---

### Post by Nick11 on 2007-12-08
Okay guys I managed to fix some things. When using EasyBCD and you want the windows menu to handle the boot options (which is necessary, well, at least in my case, for stability and to stop Grub problems):

1.) Add Linux as an entry, name it anything you want, and select the correct partition, and **make sure** you click in "Grub isn't installed to the bootsector" to allow easyBCD do "its thing" and properly get Grub to work. 

2.) Make sure Vista is still in the selected entires (DO NOT get ride of this =[] ).

3.) Under "Change Settings" you will be able to select you default OS and timings.

4.) **If you want Windows to handle the boot options**- under "Manage Boot Loader" click "Write MBR, with the "Reinstall the Vista Bootloader" checked in. 

____________________________________________________________________________________

**If you somehow mess up your boot options and cannot start an OS:**

Go to the command prompt in your recovery Vista DVD via recovery options. If you only have it on a partition (and to do not have it on a DVD), then you must reinstall Ubuntu and access it though the GRUB menu. 

Next, go to your command prompt (under advanced options usually). Then type in the following:

bcdedit /export C:\BCD_Backup

ren c:\boot\bcd bcd.old

bootrec /rebuildbcd

This will reset your BCD settings back to default allowing you to access Vista through GRUB once again. (You may have to select the second option of Vista now if you have it on a partition, and it will bring up another sup menu to select the Vista OS).

I really hopes this helps some people out with Vista, and want whose objective is to dual boot with Ubuntu.

---


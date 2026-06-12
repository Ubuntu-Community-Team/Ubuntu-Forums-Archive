---
title: "First Grub error, now won't even display bios"
date: 2013-03-23
forum: General Help
---

### Post by ChrisHayes93 on 2013-03-23
My whole problem started when I deleted Ubuntu from my desktop. I previously had dual booted with windows 8. I was finding much use for ubuntu since I do a lot of gaming and getting windows games working on ubuntu seemed like a confusing process. Anyway, after following a tutorial I seen online I deleted the memory on the partition that I had dedicated to ubuntu. The problem was, I couldn't expand the windows partition back into that one. Therefor I had unallocated space on my hard drive. I didn't think anything of it to be honest cause I'm a beginner at this kind of stuff; I have a lot of experience with computers overall though. So the next time I restarted my computer it was comming up with a black screen which read something along the lines of grub error gbt7. I can't exactly remember. I tried a number of things to fix this including software called liveboot. Nothing seemed to be working for me. I decided maybe I could at the least run ubuntu off of my External Hard Drive and use boot repair and be done with the problem. I couldn't seem to get it to boot from my hard drive, so I went into BIOS and carelessly disabled legacy boot thinking that had something to do with it. I restarted my computer and now it just beeps 6 long beeps and for every beep it flashes the yellow power light. Can anybody help me come up with a solution? I don't care if it means I have to buy new hardware, I just want my computer back.

---

### Post by oldfred on 2013-03-23
What computer?
Some with the right keys will still get you into UEFI/BIOS.
Did you have fast boot on? That often is the issue as it bypasses UEFI and goes straight to Windows. But then if Windows does not work.....

Some info others have posted
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive

      
 UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.
Windows 8 POST is so fast that boot from disk is disabled by default, here's how you do it instead.
[http://ubuntuforums.org/showpost.php?p=12525520&postcount=20](http://ubuntuforums.org/showpost.php?p=12525520&postcount=20)

Is this a system that you can remove drive? Then from another system you may be able to fix the efi partition to let you boot. Becomes difficult if other system is not UEFI, I think. But Boot-Repair can run from BIOS/CSM and run efi fixes.

---

### Post by ChrisHayes93 on 2013-03-24
It's an Hp Envy H81410. Before, when it atleast had a display and showed errors, I tried to recover my PC but it didn't work, I believe the unallocated space on the partition is to blame for this. I'm going to try and get rid of the beeping using the links you provided first then I guess we'll get back to that problem... Baby steps. Thanks for the reply.

---

### Post by ChrisHayes93 on 2013-03-24
I failed to mention that the ONLY thing it does is make 6 long beeps and the yellow flashing lights. My monitor doesn't come on or anything but I can hear everyfan running.

---

### Post by oldfred on 2013-03-24
For motherboards that have beeps, that means something. You have to look in your computer manual (or online) and see what 6 beeps means for your model.

---

### Post by ChrisHayes93 on 2013-03-24
So I resolved the beeping by removing the battery from the motherboard then putting it back in its place. Now I'm back to the original problem.... Getting windows 8 to run I found a windows 8 installation cd and went to the place where it say repair my computer, when I try to reset/restore windows 8 I get this message "unable to reset your pc a required drive partition is missing windows 8" keep in mind that I still have my LiveUSB with ubuntu on it if I need to change anything in GP Partition manager. Can Someone tell me what it is I need to be doing?

---

### Post by oldfred on 2013-03-24
If it is Windows 8 pre-installed you have to convert the standard install to UEFI install?

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---


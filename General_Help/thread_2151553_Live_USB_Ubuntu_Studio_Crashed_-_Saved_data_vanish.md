---
title: "Live USB Ubuntu Studio Crashed - Saved data vanished??"
date: 2013-06-04
forum: General Help
---

### Post by scathe on 2013-06-04
I've been combing the webs and this forum for an answer, and couldn't find it. I'm kind of lost as to what's going on here and how to fix it.

Basically, I was using Ubuntu Studio via live USB (configured by YUMI) because my current Studio permanent installation was borked and I needed to conduct an interview that very moment. I got the interview done, saved it to a hard drive partition (FAT32; not C:\ where Win7 lives in NTFS), and then moments later my cat stepped on the power strip. Bam. Computer off.

I wasn't worried about it, however, because my data had saved and I'd verified that it was there, right? Well, turn the machine on today and, lo and behold, nothing there. The data is gone. I tried recovering it from the partition via Recuva and testdisk and there's nothing there, either.

Is there any way to recover this? Would the Audacity recovery cache still be findable on the USB stick, or am I looking in the wrong place, here? Why would data saved to another drive be affected by the LiveUSB crashing, anyway?

Thanks in advance.

---

### Post by Mark Phelps on 2013-06-05
Do you Hibernate Win7 when it's not being used? Asking because with Hibernation, any open partitions are returned to their previous state when Win7 is restarted.  This means any changes made to those partitions is LOST when Win7 is restarted.

Also, you could try following the instructions below to see if the Runtime Software app does any better job of finding the lost file.  It's free to try; it costs money to actually use: 

[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by zequence on 2013-06-09
Saving onto the live usb will not save files permanently. The home folder is virtual, living in RAM only. 

In order to be able to save onto the usb stick, one needs to create a separate partition for that, and use that, instead of the user home folder.

---


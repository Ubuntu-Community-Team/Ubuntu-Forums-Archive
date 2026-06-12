---
title: "How to move MBR/Grub from Disk 1 to Disk2?"
date: 2007-05-31
forum: General Help
---

### Post by talatnat on 2007-05-31
Through some convoluted circumstances (hard-disk crashes, my ignorance), my computer now has this structure

1. SATA 250GB, sda, Grub on MBR, two partitions corrupted, a small FAT32 usable. 
2. SATA 250 GB, sdb, and in this order: Mac OS X, Ubuntu Edgy, Win XP, Edgy Swap, FAT 32, and NTFS partitions.

Here's what happens when I try booting in various combinations:

a. If I boot off sda (Master), and sdb (Slave), I can get Grub to let me boot to any of the three OSs. All is fine here.
b. If I boot off sda (Master), and sdb is disconnected completely, I get a "Grub Error", indicating there is Grub on sda.
c. If I boot off sdb (as Master) and sda (Slave or disconnected entirely), I get a frozen computer needing a hardware reset.
d. If I use SuperGrub to boot off individual partitions on sdb, I can only boot of the Ubuntu sector (hd1,1); both the Mac (hd1,0) and XP (hd1,2) partitions just end with a blinking cursor and nothing else. 

I'd like to move the Grub on sda to sdb, and still be able to triple boot. The goal is to reformat sda, and then use it for backup or for reloading a cleaned up system via dd from sdb to sda in the traditional triple-booting order: XP, Edgy, Mac.

 I'm afraid that if I just start to dd from sdb to sda that I might overwrite the current MBR/Grub and make the whole system unusable. I don't know enough on how to move MBR/Grub from sda to sdb, and where to put it on sdb.

Or, maybe I'm looking at it completely wrong, and there's a better way out of this mess. What would be the best and safest way to reclaim sda? 

Thanks for any advice/pointers.

---

### Post by eyelessfade on 2007-06-01
I think you should just boot up with sda and start ubuntu from sdb. when booted run grub-install and make it install on sdb with mbr. now you can throw away sda, technically :)

hope i understood what you wanted :p

---

### Post by talatnat on 2007-06-02
Thank you, eyelessfade. You gave me the confidence that there was a simpler solution.

I don't think it will affect what you suggested I do, but I thought I'd best double-check with you before proceeding (I still have not done grub-install).

I re-read the Grub manual to do things right, and re-checked what I had posted before and noticed some differences (probably because I don't know exactly what I am doing). Anyway:

a. sda+sdb > boots all three OSs fine via Grub menu: Ubuntu, XP, Mac
b. sda (sdb disconnected) > Grub Hard Disk Error
c. sdb (sda disconnected) > Goes to Mac OS X **OR** Win XP automatically (the first and third OS installed on sdb)
d. sda (boot from MBR, via Supergrub) > boots all three OSs fine via Grub (so Grub is on MBR)
e. sdb (boot from MBR, via Supergrub) > Error loading operating system
f. sdb (hd1,0, via Supergrub) > blinking cursor (this is the Mac OS X parttion, the first OS I loaded on sdb).
g. sdb (hd1,1, via Supergrub) >  boots all three OSs fine via Grub menu: Ubuntu, XP, Mac
h. sdb (hd1,2, via Supergrub) > blinking cursor (Win XP is the last OS loaded on sdb).

The differences between my first report and this one are that: sdb (with sda disconnected) now goes to Mac or XP (before I got a blinking cursor). I'm not sure why the OSs switch, but maybe different partitions were active at the last reboot?

Quick question: Why and what  are the differences between (c), (e), (f) and (h).

Any last minute tips on how to proceed (like what grub, MBR type files to back-up?) I just don't know enough to proceed confidently (no matter how much I google).

Thanks again.

---

### Post by talatnat on 2007-06-02
Okay, I took your advice and did a grub-install on MBR of sdb -- no errors.

But I couldn't boot into any of the three OSs (Grub error 17: Cannot mount partition). Of course, it was looking at sda, so I changed boot order in BIOS, changed device.map, and menu.lst, and now everything WORKS!

Thanks again eyelessfade!

(You said: now you can throw away sda, technically:)... Well, just for the heck of it, I disconnected sda, and Ubuntu just starts booting and then hangs for about two minutes before I gave up and rebooted with sda connected. I guess I need to delete sda from the device.map or something, but since I need to use sda anyway as a backup, no worries!)

Thanks again.

---

### Post by CrucifiedEgo on 2007-06-02
> **talatnat said:**
> Okay, I took your advice and did a grub-install on MBR of sdb -- no errors.

But I couldn't boot into any of the three OSs (Grub error 17: Cannot mount partition). Of course, it was looking at sda, so I changed boot order in BIOS, changed device.map, and menu.lst, and now everything WORKS!

Thanks again eyelessfade!

(You said: now you can throw away sda, technically:)... Well, just for the heck of it, I disconnected sda, and Ubuntu just starts booting and then hangs for about two minutes before I gave up and rebooted with sda connected. I guess I need to delete sda from the device.map or something, but since I need to use sda anyway as a backup, no worries!)

Thanks again.

Hey,

When you figure this out, can you post the fix?  I'm in the exact same predicament, having *borrowed* an IDE drive to backup the data off of my 2 SATAs, installed ubuntu on SATA1 and it decided to install the MBR on the borrowed drive.  Unfortunately, i didn't notice it until I spent about 4 hours getting both ubuntu and XP configured to my and my wife's likings, respectively.  Would be greatly appreciated!

-J

---

### Post by statictonic on 2007-06-02
[http://ubuntuforums.org/showpost.php?p=1769691&postcount=5](http://ubuntuforums.org/showpost.php?p=1769691&postcount=5)

That should help, you need to setup grub on the second drive, so do HD1

You can do this from ubuntu if it's booting fine, otherwise just boot off an ubuntu cd.

sudo grub

root (hd1,whateverpartitionforubuntu)

setup (hd1)

---

### Post by confused57 on 2007-06-02
> **CrucifiedEgo said:**
> Hey,

When you figure this out, can you post the fix?  I'm in the exact same predicament, having *borrowed* an IDE drive to backup the data off of my 2 SATAs, installed ubuntu on SATA1 and it decided to install the MBR on the borrowed drive.  Unfortunately, i didn't notice it until I spent about 4 hours getting both ubuntu and XP configured to my and my wife's likings, respectively.  Would be greatly appreciated!

-J
Use the live cd to install grub IPL to your SATA1 mbr:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)
instead of "setup (hd0)", you'll probably do "setup (hd1)", whatever "find /boot/grub/stage1" shows
Added:  Didn't realize statictonic had already suggested this.

Then boot first to your SATA1 drive, if you get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hdx,y) to (hd0,y), then press "b" to boot...this is temporary, but if it works you can make it permanent in your menu.lst.

---

### Post by talatnat on 2007-06-03
I did pretty much what is suggested above, except that I used grub-install, as eyelessfade suggested, and it was pretty easy. If things don't work for some reason, just boot of a live CD or Supergrub and check boot/grub/menu.lst and boot/grub/device.map to see that they are pointing to the right drive and partition. I had to do some minor edits, like change  (hd0,0) to (hd1,0) and sda to sdb. You may also have to change the hard-disk boot order in BIOS.

---

### Post by cemptor on 2007-06-09
I have teh exact same problem as CrucifiedEgo

I reinstalled my grub to hd(1,0) using grub-install and it gave me no errors.

However no change.

My Windows and Fiesty are both on the seond SATA drive(sda), and the original PATA drive(hda) is empty. However I can never boot unless the PATA drive is the first to boot. If hda is disconnected (which is my goal) I get the grub menu with the listing of OS, but all of them lead to "error 22": cannot find operating system

Edit later:

Never mind. I realized that the disk address in my menu.lst was wrong! I had it booting from hd(1,0), which is no longer valid if I disconnect the second drive. All I had to do was change that and it's working.

Thanks!

---


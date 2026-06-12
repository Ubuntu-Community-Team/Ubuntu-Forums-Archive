---
title: "Computer freeze then reboot failure"
date: 2016-08-26
forum: General Help
---

### Post by fbdonaldson on 2016-08-26
Hello everybody,

MSI Military Class 4 MB A78M-E35 using SSD for O/S & HDD fordata. Ubuntu 15.10 O/S

My desktop freezes in unpredictable way requiring a full reboot that very predictably leads to problem of boot sector not being detected; 'please install etc' on black screen.At this juncture, instaed of rebooting that continues to fail, I leave the computer for some time (hours) when it usually fires up as normal.

I have done 'boot.repair' in the terminal and got a 'successful' outcome except that the problem persists. The report is at: 

[http://paste.ubuntu.com/23078032](http://paste.ubuntu.com/23078032)

The repair message also says: 'The boot files of Ubuntu 15.10 are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a / boot partition(EXT 4 >200MB, start of disk). Then it refers to gParted.

Well, I'm a little overwhelmed by now so I am throwing this to you folk for HELP.

---

### Post by mook765 on 2016-08-27
The message not only refers to gParted, it refers also to:
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
See step 4...
Reduce the size of sda2 to get some free space between sda1 and sda2, Then create a new small partition there (about 1 GB). Remember the name of this partition (**sdaX**)
In step 6 "OS to boot by default" = sda2, "separate /boot partition" = **sdaX**, "place GRUB into" = sda1
Please refer to [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual) too...

---

### Post by fbdonaldson on 2016-08-27
Thanks for the reply. I am going to try this but currently, I can't even get the computer to even boot to the boot menu. Will have to let it cool off for a day after which it should start. See how we go then.

---

### Post by fbdonaldson on 2016-08-30
Well the days wait didn't help still not being able to get into the boot area.

Getting pretty desperate until I saw mentioned how someone had changed the drive cable to a different SATA port: I tried and got immediate results leading to satisfaction that it is working OK. 

Did another boot repair and the results are at: [http://paste.ubuntu.com/23106574/](http://paste.ubuntu.com/23106574/)

Still saying that boot section is too far from start of drive but I'd rather not dabble with unfamiliar territory if things are working. Am finding my mouse a bit juddery however.

Will leave this thread open another day for comment if that is permissible.

---

### Post by fbdonaldson on 2016-08-31
Nope, problem has returned unfortunately. This happened after some fairly heavy video traffic and news service viewing. Computer freeze and then 'no boot detected' at reboot.

Believe that I have two problems so first I want to use GParted to fix the boot problem as mentioned in the above exchanges.

Haven't got far as the the GParted 'resize window'  (/dev/sdb2) doesn't look much like that described above. I know that I am operating in a smaller , solid state drive than the above and I get this result: Min and Max sizes are the same; New Size(MiB) is also the same value and the 'Resize" button is greyed out!

So I'm trumped at first base; hope someone can assist here, please.

---

### Post by fbdonaldson on 2016-08-31
Nope, problem has returned unfortunately. This happened after some fairly heavy video traffic and news service viewing. Computer freeze and then 'no boot detected' at reboot.

Believe that I have two problems so first I want to use GParted to fix the boot problem as mentioned in the above exchanges.

Haven't got far as the the GParted 'resize window'  (/dev/sdb2) doesn't look much like that described above. I know that I am operating in a smaller , solid state drive than the above and I get this result: Min and Max sizes are the same; New Size(MiB) is also the same value and the 'Resize" button is greyed out!

So I'm trumped at first base; hope someone can assist here, please.

---


---
title: "update-grub takes a long time to finish"
date: 2015-06-24
forum: General Help
---

### Post by joe_schmo2 on 2015-06-24
I recently installed Ubuntu 15.04, it took over 4 hours to install but it did install and seems to be working fine.  I was having an issue with Ubuntu booting to an initramfs prompt and I had to type exit to continue, well I found the resolution to that problem here and I had to run update-grub.  The update-grub process took over 1 hour to complete, while running I repeatedly saw an Input/Output error on /dev/sda, not sure if that has anything to do with it or not.   I have 4 partitions on my hd, the first 2 are for Windows and the other sda3/sda4 are for Linux, sda4 being reserved for swap.

Any ideas as to why it takes so long to complete?

---

### Post by dino99 on 2015-06-24
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

you does not tell us how that installtion has been made, but that looks strange and unusual. How many partitions are 'primary', and is your mobo has a bios or uefi ?

---

### Post by oldfred on 2015-06-24
Grub typically scans all partitions to find boot files. But if any partition has issues, it does not seem to time out quickly and skip it.
I might run chkdsk on both of your NTFS partitions. If any errors rerun until no errors.
It also would not hurt to run fsck on all ext4 partitions.

Then also in Disks and icon in upper right is Smart Data. That will give a status of drive. It can run lots of tests, but passed is all I know. If not passed then time for a new drive.

---

### Post by joe_schmo2 on 2015-06-27
I have run chkdsk and fsck and neither reported issues.  It's weird, linux sees issues but I can't narrow down what the issues are.  As I said before I installed linux but it took forever, update-grub works, but takes forever.  So everything works, just very slowly, guess I'll just have to live with it for now.

---

### Post by Vladlenin5000 on 2015-06-28
> **joe_schmo2 said:**
> (...) while running I repeatedly saw an **Input/Output error on /dev/sda**, not sure if that has anything to do with it or not.
(my bold)
That really suggests a serious issue with that drive. Are you sure the tools gave no errors?
The unusual time it took to install or update-grub is consistent with a failing drive (actually one already in a very bad shape).

---

### Post by joe_schmo2 on 2015-06-28
You may be right about my hard drive being in bad shape but until I tried to install Ubuntu I haven't had any indication that there was an issue.  I have run chkdsk /R, I guess I could try other options.  I've also booted to a USB drive and run fsck.

I've tried finding a good utility that would help me but nothing I try indicates any serious issues.

---

### Post by oldfred on 2015-06-28
In Disks and icon in upper right corner of Disks is Smart Status on hard drive. 
It can run lots of tests on hard drive but passed or a good drive is all I really know.

Windows often happily keeps running and then fails catastrophically. And drives do fail. But often Linux starts to see issues and gives you a bit more time to make sure your backups are current, but not even always. Or make sure you have good backups.

---

### Post by monkeybrain20122 on 2015-06-28
Four hour installation is absurd. It takes 10 minutes here for 15.04. I agree that your drive is failing.

---

### Post by joe_schmo2 on 2015-06-29
Hope it doesn't completely fail for a long time, I really need this laptop and I am broke.

---

### Post by monkeybrain20122 on 2015-06-29
> **joe_schmo2 said:**
> Hope it doesn't completely fail for a long time, I really need this laptop and I am broke.

Did you check the SMART status as oldfred asked you to? What are the results?

It will cost a lot less to replace the hard drive than to get a new laptop. I would not use a computer knowing that the hard drive is dying, one day you may lose all your data out of the blue.

---

### Post by joe_schmo2 on 2015-07-01
> **monkeybrain20122 said:**
> Did you check the SMART status as oldfred asked you to? What are the results?

It will cost a lot less to replace the hard drive than to get a new laptop. I would not use a computer knowing that the hard drive is dying, one day you may lose all your data out of the blue.

I did do as oldfred suggested.  Although all the individual tests pass, it says "Self-Test Failed"

I do see under the "type" column a lot of "Pre-Fail" and "Old Age", but all of the "Assessment" columns say "OK"

---


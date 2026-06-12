---
title: "Unable to mount the drive"
date: 2013-03-12
forum: General Help
---

### Post by hiteshkataria on 2013-03-12
I have a 500GB Hard drive, which is partitioned into 3 sub drives using Windows 7. Now when I switch on my laptop, it is not getting booted and I'm getting an error message Error code: 0142.
So I have installed Ubuntu 10.10 and I am able to use my laptop. However when I try to access one of the drive, I get the below error message (I'm able to access the other 2 drives with no issues):

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Can you please let me know how can I resolve this.

Thanks.

---

### Post by schragge on 2013-03-12
Quick googling [shows]("http://en.community.dell.com/support-forums/disk-drives/f/3534/t/19241209.aspx") that error code 0142 is specific to Dell and usually means some hard drive hardware problem.

---

### Post by hiteshkataria on 2013-03-12
> **schragge said:**
> Quick googling [shows]("http://en.community.dell.com/support-forums/disk-drives/f/3534/t/19241209.aspx") that error code 0142 is specific to Dell and usually means some hard drive hardware problem.

Thanks, schragge!
So replacing hard drive is the only solution or we can use the existing one?

---

### Post by Mark Phelps on 2013-03-12
Have you tried doing what it suggested:

> In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! 

If that fixes the partition, you should be OK.

---

### Post by schragge on 2013-03-12
Also, have a look at this thread:
[http://www.pcguide.com/vb/showthread.php?69036-Dell-Error-Code-2000-0142](http://www.pcguide.com/vb/showthread.php?69036-Dell-Error-Code-2000-0142)

---

### Post by hiteshkataria on 2013-03-27
Thank You!
I'm able to access the drive.
I inserted OS disc and booted from disc and selected repair. I did not work, tried 3 or 4 times and ran Memory tests. And finally I'm able to login in Win 7 as well as ubuntu.
Thanks a lot!

After logging into Win 7, I tried with chkdsk command but it showed message stating the disk volume is used by other process(don't remember the exact message).

I'm not sure how long will my drive be Safe. Is there any action to be taken? Please advice.

---

### Post by CatKiller on 2013-03-27
Backup your data.

---

### Post by el puma inmundo on 2013-03-29
I am relatively inexperienced with Linux.  I have been using a Samsung M2 320 GB external hard drive for over a year and a half.  I am now operating with Ubuntu 12.04 Precise.  Today, I began having problems mounting the hard drive and receive the following error message:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

The computer doesn't have Windows installed, and I don't know what to make of the error message.  That I know of, the hard drive hasn't received any trauma recently.  I did install a sizeable update the other day, but I don't know that that would affect the hard drive's performance.  Any suggestions?  Thanks.

---

### Post by schragge on 2013-03-29
While there is [ntfsfix](http://manpages.ubuntu.com/manpages/precise/en/man8/ntfsfix.8.html) command and you may try it on your drive, you usually need a Windows machine to repair a damaged NTFS filesystem.

---

### Post by Mark Phelps on 2013-03-29
Sorry, only Windows can repair NTFS file systems.  Normally, when you request that CHKDSK to be run on a Windows volume, it tells you the volume is busy and asks you if you want to schedule a disk check on the next boot.  In that case, you reply Yes, and when the machine reboots into Windows, it runs CHKDSK first.

What I would suggest you at this point is the following:
1) Find a working Windows PC
2) Download the ISO file for the Minitool Partition Wizard Boot CD on that PC and burn a CD from that
3) Insert the CD in your PC and boot from it
4) When Partition Wizard starts, select the option to Check the drive -- that will run chkdsk on that drive

---

### Post by el puma inmundo on 2013-03-29
Thank you.  I appreciate your responses.  I'll give chkdsk a try.

---

### Post by el puma inmundo on 2013-03-30
Mark Phelps,

I followed your suggestions.  The Windows machine would not recognize the hard drive in order to scan it.  I downloaded the MiniTool Partition Wizard and booted from the CD, I haven't been able to check the file system.  The Wizard says that the drive needs to be lettered in order to be checked, but when changing the letter (or labeling the drive with a letter) appears as an option that can't be selected from the menu.  I've tried reading the help and looking for answers on the internet, but everything is a dead end.  Any words of advice?  Thank you.

---

### Post by el puma inmundo on 2013-03-31
I successfully checked and repaired the drive using Partition Wizard on a Windows machine (the boot CD version doesn't contain this option).  I was able to read the drive on said machine, but when I tried mounting it on my Linux laptop, no go.  I am checking and repairing again on the Windows machine.  What ought I do when it finishes?  Thanks again for your responses.

---


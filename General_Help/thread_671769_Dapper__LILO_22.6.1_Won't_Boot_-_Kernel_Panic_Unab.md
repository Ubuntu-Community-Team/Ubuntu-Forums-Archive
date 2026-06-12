---
title: "Dapper / LILO 22.6.1 Won't Boot - Kernel Panic: Unable to Mount Root FS"
date: 2008-01-18
forum: General Help
---

### Post by rsioss on 2008-01-18
My system has been running for quite some time, and was originally set up with Breezy, and upgraded to Dapper a long time ago.  The system is single boot with two IDE drives configured in Raid 1.  Earlier today the system was unresponsive, and I had to do a hard reboot.  Now when the system tries to boot, I see several errors:

RAMDISK: Couldn't find valid RAM disk image starting at 0
VFS: Cannot open root device "FD00" or unknown-block (253,0)
Please append a correct "root=" boot option
Kernel Panic - Not syncing: VFS: Unable to mount root FS on unknown-block (253,0)

Can anyone provide me with some troubleshooting pointers / steps?  I have tried Googling and searching the forums here, but I have not been successful in finding troubleshooting procedures.  I am assuming that the first step will be to boot the system with the recovery CD, so I am downloading the Dapper install media now (the only media I have is from the Breezy install that I had originally used).  Assuming I am able to boot from the CD, what should I do next?

Thank you in advance!
-Rob

---

### Post by tgalati4 on 2008-01-19
First, what kind of RAID did you have set up?  Mirrored for reliabilty? or Striped for speed?

Boot the Live CD only from now on until we learn a little more about what happened.

What was the estimated uptime until failure?  Is the machine on an UPS that works?

It could be a drive bearing failure.  How old are the drives and what is the make and model of the drives?  A google search on your drive model will reveal common problems that folks are having with your type of drive.

When you boot the Live CD, try to mount at least one drive and see what you can see.

It could be as simple as a corrupt partition table which can be fixed with little consequence.  It could have been a power supply problem that caused a blackout which corrupted your partition table.  So what looks like a wonky hard drive could really be an aging power supply.  How old is the machine?

---

### Post by rsioss on 2008-01-19
I have RAID 1, which is mirrored for reliability...  The uptime before failure was varied because the two drives were purchased at different times.  The master drive has been in the machine since it was purchased, so it's about 7 years old (which is the approximate age of the machine).  The slave drive is only about a year or two old.  I believe one of the drives is a Western Digital and the other is a Seagate, but I'll have to double check that. The drives weren't making any noticeable noises or anything, and it's been my experience in the past that when a bearing is going bad it can get noisy.  I know I can't rule this out, but I just wanted to mention it.  Yes, the machine is on a working UPS.

In some of my searches that I had done prior to posting, it sounded like it could possibly be a corrupted LILO configuration, but I didn't know how to troubleshoot that either.

After booting from the Live CD, is it fairly straightforward to mount the drives?

---

### Post by rsioss on 2008-01-21
PROBLEM SOLVED!!!

It turns out I was able to successfully boot my system using the LinuxOLD boot image.  I had never had to do anything other than allow LILO to boot the default image before, so I was not aware of this possibility as a troubleshooting measure.  

Once I realized that I was able to boot the old image successfully, I tried another reboot with the default boot image, and it failed in the same manner.  There must have been something wrong with that particular image.  I rebooted into the old image again, and installed all available updates (one of which was a kernel update).  

I was then able to boot up successfully with the now updated default image.  I also realized during startup that I was seeing a message that my RAID was no longer starting up properly:

```
kernel: [17179579.544000] md: kicking non-fresh hdb1 from array!
```

Through some more searching around, I found out that I needed to use mdadm to add the drive back into the array, and allow it to recover the data:

```
mdadm --manage /dev/md0 --add /dev/hdd1
```

To monitor progress, you can look at the contents of /proc/mdstat periodically.

---


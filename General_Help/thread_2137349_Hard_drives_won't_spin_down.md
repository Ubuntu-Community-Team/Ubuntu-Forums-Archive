---
title: "Hard drives won't spin down"
date: 2013-04-20
forum: General Help
---

### Post by VanderveckenSmith on 2013-04-20
Hi all,
I have a bunch of hard drives in an external enclosure, and I want them to standby after a certain period of time.  I have XUbuntu 12.10 (up-to-date) and I open the Disks application in Settings Manager, and set every disk in the enclosure to have a standby time of 20 minutes.  Then I specifically set one of the 8 disks to immediately standby using the command in the GUI (I hear the disk spin down).
25 minutes later, I come back and check the disks with hdparm -C /dev/sd*
The disk that I specifically spun down is still on standby.  The disks that I just set to have a timer of 20 minutes have not spun down.
The disk array is a raidz2 pool, so I'm pretty sure it's not the case that all 7 other disks were accessed but the one I put on standby was not.  It seems more likely that Ubuntu is simply not respecting the standby timer setting.  I tried it also with explicit hdparm -S 240 /dev/sd* and it still didn't work.

What can I do to make the system properly standby drives after a designated time?

Thanks,
Vandervecken

---

### Post by tgalati4 on 2013-04-20
Standby and RAID (Z or not) is a dangerous combination.  If you set up your disks as JBOD (just a bunch of disks) then each disk is independent and standby should work correctly.  If you have any system files on the raid pool then it will wake frequently.

---

### Post by VanderveckenSmith on 2013-04-21
You are right that if I have any system files on the Raid it will wake frequently.  However, I don't.  The RAID is purely a data store for a media PC.  It only has media on it.  I anticipate the system will wake at most 4-5 times a day, and that's not a problem for the lifetime of the disks.
Given that, I don't understand why standby isn't working correctly.  I also note that as I said above, the one disk I did set explicitly to standby remained asleep for hours without waking.

---

### Post by VanderveckenSmith on 2013-04-23
Can anyone help?

---

### Post by dino99 on 2013-04-23
As said into post # 2, you are trying some illogical task
check that hddtemp is not installed/running
and rework your raid pool: set the hdds to spin down outside the raid pool.

---

### Post by tgalati4 on 2013-04-23
If I have read your post correctly, you are running a RAIDz2 pool which implies running ZFS file system across several drives.  ZFS is not a native file format for linux, so you are running a wedge, either fuseZFS or a ZFS kernel module to be able to talk to the disks.  So, by definition, your raid pool is a system disk--regardless of what files you have on it.

I am running a freenas NAS that I built using several terabyte disks also running a ZFS pool.  My disks spin down after 8 or 12 minutes (I can't remember what I set.)  I have to wait 7 seconds for the disks to spin up when I access the media over the network.  But it works.  ZFS is native to BSD and standby seems to work correctly.

If you had used a standard mdadm raid pool, then you have a chance at getting standby/spindown to work, but I don't have any experience with mdadm on my network, so others will have to chime in on how well disk spin down works with standard software pools.

ZFS periodically scrubs the data to check integrity, so using standby/spindown adds some risk to the both the filesystem and any raid pools defined.  It is generally not recommended, nor are "green" drives recommended for any raid.

---

### Post by VanderveckenSmith on 2013-04-24
ZFS does not periodically scrub, it scrubs when I tell it, but just to be sure, I restarted the computer without mounting the Raid pool.  Now all I have are a bunch of disks.  They still do not spin down!  I hdparm -Y one of them (forcing it to spin down) and it stayed spun down.  The other disks did not spin down after the time interval set in Ubuntu settings.

So this is clearly not a RAID issue.
It's also not an issue of periodic access.  If it were, the disk I forcibly spun down would have spun up by itself because of periodic access.  It hasn't.  Also, hddtemp is not installed.

---

### Post by tgalati4 on 2013-04-25
Are they any disk-related power settings in your BIOS?  Sometimes the BIOS settings can interfere with power management being performed by the operating system.  Also, was the one disk that you forcibly spun down formatted with ZFS?

---

### Post by VanderveckenSmith on 2013-04-29
Sorry for the late reply.  There don't seem to be any power settings in  the BIOS that interfere.  Additionally, the drives are in an external  enclosure, so they shouldn't be affected by BIOS settings.
I took out  a ZFS drive from the external enclosure and put in a regular drive  instead.  Same problem, it didn't go to sleep, even though I set it for  30 minutes standby.

---


---
title: "Grub messed up MBR--how do I fix?"
date: 2007-05-20
forum: General Help
---

### Post by megagram on 2007-05-20
Hey guys, I'm really hoping somebody can help me out here: before I start, I am not blaming grub for doing this to my drive as my power supply was messing up big time and resetting my computer.. I finally replaced it but when I booted up grub wouldn't load on the drive. So I tried reinstalling grub but it failed and now it seems my partition table is royally messed up.

It originally had one NTFS for winXP, one Ext3 for Ubuntu and one HFS+ for messing around with Mac OS X... The only partition I care about rescuing is the NTFS one.

The drive, after running SeaTools on it was reporting tons of SMART errors. I did a zero-out data on it and the errors seem to have gone away. I then DD'd the data back on to the drive (unfortunately I DD'd it _after_ the messed up grub install).

So I would like to know what my best course of action is in dealing with repairing my partition table. Thank you.

---

### Post by jimrz on 2007-05-20
> **megagram said:**
> Hey guys, I'm really hoping somebody can help me out here: before I start, I am not blaming grub for doing this to my drive as my power supply was messing up big time and resetting my computer.. I finally replaced it but when I booted up grub wouldn't load on the drive. So I tried reinstalling grub but it failed and now it seems my partition table is royally messed up.

It originally had one NTFS for winXP, one Ext3 for Ubuntu and one HFS+ for messing around with Mac OS X... The only partition I care about rescuing is the NTFS one.

The drive, after running SeaTools on it was reporting tons of SMART errors. I did a zero-out data on it and the errors seem to have gone away. I then DD'd the data back on to the drive (unfortunately I DD'd it _after_ the messed up grub install).

So I would like to know what my best course of action is in dealing with repairing my partition table. Thank you.

try booting from your windows cd, go to the recovery console and type:
```
fixmbr
``` 
hit enter, then reboot. then, if the drive is not totally hosed, it should take you to your normal win boot.

---

### Post by megagram on 2007-05-20
Thanks for the reply. How does fixmbr work? Will it repair an obviously corrupted MBR? In DiskDirector, there are 5 partitions listed (had 4 originally) and 4 of them are tiny and the fifth is 67gb and listed as invalid. The drive is physically only 40GB.

Thanks.

---

### Post by jimrz on 2007-05-21
> **megagram said:**
> Thanks for the reply. How does fixmbr work? Will it repair an obviously corrupted MBR? In DiskDirector, there are 5 partitions listed (had 4 originally) and 4 of them are tiny and the fifth is 67gb and listed as invalid. The drive is physically only 40GB.

Thanks.

i believe it just overrights the boot sector with a brand new mbr pointing to your win partition (1st active partition on the drive), though it may be more than that. unfortunately, what disk director is reporting seems to indicate much bigger problems than just a hosed mbr. 
if fixmbr does not work and the drive is toast, try a "live cd" to try to save what data you can. if any of the partitions you show contain your data and can be mounted you may be able to back up to an external or another internal drive

---


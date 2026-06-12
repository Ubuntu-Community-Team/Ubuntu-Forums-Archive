---
title: "Having errors trying to mount an NTFS drive."
date: 2017-02-04
forum: General Help
---

### Post by Micronic on 2017-02-04
I am running ubuntu on a live USB.  I am trying to mount the hard drive on a laptop that has Windows 7 installed.

```
mount -t ntfs-3g /dev/sda2 /media/windows -o force
```

The message I get is:
```
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda2)?  Or the other way around?
```

Does anyone know how I can mount this drive?  (I ran fdisk -l and I know it is /dev/sda2)

---

### Post by howefield on 2017-02-04
Use the paperclip icon from the "*Reply to Thread*" feature to attach your image to your posting.

---

### Post by oldfred on 2017-02-04
You are showing RAID which is how Linux sees Intel SRT.
Does you system have a small SSD which is used just for Booting as a location for the hibernation for fast start up.
Windows boots so slow they made vendors modify hardware to make it seem like it boots faster.

See what this says, you may have to install mdadm. 
 sudo mdadm --detail-platform 

      
 dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
But I do not know if dmraid is still better option for Intel SRT type RAID or not.


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
[QUOTE]Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

---

### Post by efflandt on 2017-02-04
From your screenshot, it is obviously a RAID partition, not a normal NTFS partition. I know nothing about RAID, but web searching "how to mount windows raid in ubuntu" could provide answers.

---


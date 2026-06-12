---
title: "Inconsistant hard drives"
date: 2007-12-23
forum: General Help
---

### Post by swinky on 2007-12-23
Hi,

I've installed Ubuntu a number of times on separate computers, but I've never encountered a problem like this before. I recently installed Ubuntu Gutsy after finally getting another hard drive so I can dual boot between Ubuntu and Win XP. The XP drive is my main drive and vastly bigger than the Ubuntu drive, so I need to be able to mount the XP drive. This is easy in theory, but something is messed up. 

Each time I reboot my computer, the hard drives will randomly decide to change names in the /dev folder. When I set up my fstab file, the Windows drive was /dev/sda, and most of the time it will mount when I boot. The Ubuntu drive is then assigned /dev/sdb. But sometimes I boot and Windows isn't mounted, and if I type "sudo mount -a" it says:
> NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


But if I type
```
sudo mount /dev/sdb1
```

It mounts fine.  Then if I reboot, it mounts correctly as /dev/sda1 during boot. Any ideas on what might be causing the drives to keep switching on me?

---

### Post by Craigus on 2007-12-23
This is extremely odd. Can you describe the hardware setup - what drives are connected to which channels ? IDE or SATA (or USB/Firewire) ?

---

### Post by swinky on 2007-12-23
My WinXP drive is a 500gb Samsung SATA drive. The Ubuntu drive is a 60gb Western Digital IDE drive. Also on the IDE cable is my optical drive. I'm not sure about the master/slave settings, could that be causing it?

---

### Post by vanadium on 2007-12-23
```
the hard drives will randomly decide to change names in the /dev folder.
```
This suggest to me that your /etc/fstab is using device names instead of UUID= or LABEL= You probably should post your /etc/fstab here.

---

### Post by swinky on 2008-01-02
So, I thought it worked itself out, since it hadn't done it for a while, then all of a sudden the problem cropped back up. But I did some research online and figured out how to get the UUID for each volume. The Linux drive was automatically set up with the UUID but the WinXP wasn't, it was set up with a the mount point /dev/sda1. So I simply changed that entry to the proper UUID and I haven't had an issue with it since.

---


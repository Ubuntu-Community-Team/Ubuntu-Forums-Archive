---
title: "Changing universal path to /home"
date: 2006-11-25
forum: General Help
---

### Post by Aerugo on 2006-11-25
A few days back, I changed my /home directory to be an external firewire drive. This has been working like a charm. But today, when I rebooted the computer for the first time since I moved my /home directory, I was met by disappointment when ubuntu couldn't find the directory on sda1, where I installed it. After pulling out a few fists of hair, I tried disconnecting my second external drive, a USB NSTF drive. And behold; it works.
It then struck me that when I moved my /home directory, I also reformatted the firewire drive from FAT32 to ext3, and while doing that, I disconnected my USB drive, so that I wouldn't format that by accident.
It seems that Ubuntu wants to mount the USB drive before it mounts the firewire one, assigning the first one sda1 and the second one sdb1.
It's a bitch always having to think about disconnecting the USB drive every time I reboot, so I want to fix this.
Any ideas?

---

### Post by CoolHand on 2006-11-25
Just edit your /etc/fstab file and set a permanent entry for the drive with your /home on it.  It is fine to leave it as sdb1 if you always have the other drive attached. An option is to not use the hardware designation.  I was just reading another post about using a hash to identify drives in the fstab file.  The entry looks like this:
UUID=5384420f-f9ae-458e-b633-adfcb197cb6a / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

You can find the hash for your drive by running sudo dumpe2fs -h /dev/sda1

Then set it in your fstab however you need it and even if it changes from sda1 to sdb1 the system should still find it using that hash.  Good Luck

---

### Post by CatKiller on 2006-11-25
A search on "UUID" will probably reveal more information if you need it. To reiterate what CoolHand said - **don't** use the number that he listed. The number you'll need will be particular to **your** partition. That is rather the point.

---


---
title: "External HDD can't unmount to format in gparted"
date: 2015-12-04
forum: General Help
---

### Post by Rocket J Squirrel on 2015-12-04
Hi, I replaced the HDD in my laptop with an SSD, and I'd like to repurpose the old HDD. I've put it in an external HD case and have connected it via USB.gparted finds it as /dev/sdb1, but I can't umount it in gparted because it says > Could not unmount /dev/sdb1The partition could not be unmounted from the following mount points  /    Most likely other partitions are also mounted on these mount points.You are advised to unmount them manually. I reckon that the other partitition mounted to / is sda1 which is needed to operate the system.sdb1 does not show up in /mnt nor /media nor /etc/mtab nor in Nautilus (actually using Lubuntu and its File Manager). So how do I unmount this thing if the OS doesn't see it but gparted does?

---

### Post by Bucky Ball on 2015-12-04
You are booting into the OS on the sdb drive by the sounds of it. Check the BIOS to make sure you are booting from sda or choose it from the boot device options (pressing F12 sometimes gets you there) at boot. That's why you can't unmount it and exactly why you are getting that error. You're running the OS from it.

The message is telling you /dev/sdb1 is mounted at /. Your root partition. There is no sda involved and no mistake there. In fact, if you have a look, you should be able to identify that sda is in fact the SSD using Gparted.

---

### Post by oldfred on 2015-12-04
If you did an image copy, then you have the same UUID on every partition on both drives.

List your UUID like either of these:
 sudo blkid -c /dev/null -o list
ls -l /dev/disk/by-id

      
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

If gpt partitioned, then you need to use gpt tools like gdisk or sgdisk.

---


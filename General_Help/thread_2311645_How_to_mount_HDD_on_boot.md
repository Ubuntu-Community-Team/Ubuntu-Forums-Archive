---
title: "How to mount HDD on boot?"
date: 2016-01-28
forum: General Help
---

### Post by wnodrog on 2016-01-28
Installed a 2nd HDD in my desktop on 14.04, could someone please point me in the right direction towards getting this drive to mount on boot? I am using luckyBackup and it will not backup to this drive as it says drive is not mounted.

---

### Post by Bucky Ball on 2016-01-28
Run this command and identify the partition:

```
sudo blkid
```

Make a mount point for it, lets say /data, in the directory /mnt:

```
sudo mkdir /mnt/data
```

Then, if is it say /dev/sdb3, mount it:

```
sudo mount /dev/sdb3 /mnt/data
```

The question would be, why isn't that partition mounting in the first place? Is this on an internal drive and hasn't been added to your fstab file or is it an external drive that is not mounting its partitions when plugged in? :-k

---

### Post by wnodrog on 2016-01-28
This is an internal drive that I managed to stumble through the install with way back when. I probably did not successfully add it to the fstab file. I access this drive though Media. How can I make (or change) my mount point correctly and add this to fstab? 

Output from blkid:

/dev/sda1: UUID="f7900a75-12f4-41be-99d3-396ae1389a03" TYPE="ext4" 
/dev/sda5: UUID="154dff9e-5ce3-489b-8c8b-4e8b2c0e97aa" TYPE="swap" 
/dev/sdb1: LABEL="2nd HDD" UUID="dcfb3e52-e7c8-4569-921b-7ed6e47bea4b" TYPE="ext4"

---

### Post by Bucky Ball on 2016-01-28
Something like this should do it:

```
UUID=dcfb3e52-e7c8-4569-921b-7ed6e47bea4b       /mnt/data    ext4    errors=remount-ro       0       1
```

Change '/mnt/data' to the mount point you want to use to mount the drive.

The UUID identifies the partition in this case rather than using /dev/sd**.

Reboot. Is it mounted with permissions?

PS: Please use code tags for terminal output. See the link in my signature for how. :)

---

### Post by wnodrog on 2016-01-28
> **Bucky Ball said:**
> Something like this should do it:

```
UUID=dcfb3e52-e7c8-4569-921b-7ed6e47bea4b       /mnt/data    ext4    errors=remount-ro       0       1
```

Change '/mnt/data' to the mount point you want to use to mount the drive.

The UUID identifies the partition in this case rather than using /dev/sd**.

Reboot. Is it mounted with permissions?

PS: Please use code tags for terminal output. See the link in my signature for how. :)

I created the mount point /mnt/data.....seems I have two mount points now. Can I delete / eliminate the other?  What do I do with this?

```
UUID=dcfb3e52-e7c8-4569-921b-7ed6e47bea4b       /mnt/data    ext4    errors=remount-ro       0       1
```

---

### Post by wnodrog on 2016-01-28
This is what I have in fstab now:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f7900a75-12f4-41be-99d3-396ae1389a03 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=154dff9e-5ce3-489b-8c8b-4e8b2c0e97aa none            swap    sw              0       0
UUID=dcfb3e52-e7c8-4569-921b-7ed6e47bea4b /media          ext4    defaults 0 

```

Remove the last line and replace it with the line you provided?

---

### Post by Bucky Ball on 2016-01-28
Yes. That is all. Then reboot. ;)

You need to open fstab with:

```
 sudo nano /etc/fstab
```

When changes made, follow instructions at bottom of screen to save and exit:

control+x, 'y', enter.

---

### Post by wnodrog on 2016-01-28
All done, HDD2 mounts after reboot and my old mount point (/media) is gone. Thank you for your help and patience, much appreciated!

---

### Post by Bucky Ball on 2016-01-29
No problems, good news and thanks for marking as solved. Enjoy! :D

(PS: I'm a Luckybackup fan myself.)

---


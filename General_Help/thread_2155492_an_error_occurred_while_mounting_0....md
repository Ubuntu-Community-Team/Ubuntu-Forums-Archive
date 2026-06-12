---
title: "an error occurred while mounting 0..."
date: 2013-06-18
forum: General Help
---

### Post by kkoz83 on 2013-06-18
Hi everybody, how are you?  I had to start this thread because the initial thread I found was closed.

I have a dual-boot running (with Windows 7) on a Samsung SSD drive.  I used the following site ([https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)) to tweak Ubuntu 13.04 to optomize my SSD.  
I did #6 (left side of page) and now I get the "an error occurred while mounting 0".  Can I get some help?

---

### Post by Pjotr123 on 2013-06-18
You probably did something wrong to the fstab line. If you post your fstab here, I can take a look at it:
```
gedit /etc/fstab
```

---

### Post by kkoz83 on 2013-06-18
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=1e97dcf2-33fa-4ab3-9f63-a3b4be2e5533 / ext4
noatime,errors=remount-ro 0 1
# swap was on /dev/sda7 during installation
UUID=27a3ced2-0945-43fc-936b-4f411a08cdaa none            swap    sw              0       0

---

### Post by kkoz83 on 2013-06-18
My output for "sudo blkid" is:

/dev/sda1: LABEL="OS" UUID="F6F09AA3F09A699F" TYPE="ntfs" 
/dev/sda5: LABEL="Image" UUID="0D691B100D691B10" TYPE="ntfs" 
/dev/sda6: UUID="1e97dcf2-33fa-4ab3-9f63-a3b4be2e5533" TYPE="ext4" 
/dev/sda7: UUID="27a3ced2-0945-43fc-936b-4f411a08cdaa" TYPE="swap"

---

### Post by Pjotr123 on 2013-06-18
> **kkoz83 said:**
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
[b]UUID=1e97dcf2-33fa-4ab3-9f63-a3b4be2e5533 / ext4
noatime,errors=remount-ro 0 1[/b]
# swap was on /dev/sda7 during installation
UUID=27a3ced2-0945-43fc-936b-4f411a08cdaa none            swap    sw              0       0

OK, I see....

The line break for sda6 is probably the culprit. It should be **one** line, not two. Erase the line break and replace it by a space, so it becomes like this:
```
UUID=1e97dcf2-33fa-4ab3-9f63-a3b4be2e5533 / ext4 noatime,errors=remount-ro 0 1
```

Then reboot. All should be well. :)

In order to prevent future errors, I'll write something about this in my manual.

---

### Post by kkoz83 on 2013-06-18
Awesome, thank you! ;)

---


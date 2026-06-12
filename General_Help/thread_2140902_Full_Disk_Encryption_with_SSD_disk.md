---
title: "Full Disk Encryption with SSD disk"
date: 2013-05-01
forum: General Help
---

### Post by eganvarley on 2013-05-01
Hi,

I installed Xubuntu 13.04 on my laptop and I choose to use the function "*Encrypt the new Ubuntu installation for security*".
Now if I look at my fstab I can see this :
```

egan@laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a392073a-f620-4abc-b1cd-0bb08a9e0319 /boot           ext2    defaults        0       2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
```

My hard disk on this laptop is a SSD and I would like to adapt my system for this disk. For this I need to use the noatime option and also the discard option (TRIM).
Why these options are not already set up in my fstab? Is it because my system is encrypted? How can I set these options properly with an encrypted system?

---

### Post by eganvarley on 2013-05-01
OK I found the answer here : [http://worldsmostsecret.blogspot.fr/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.fr/2012/04/how-to-activate-trim-on-luks-encrypted.html)

First you need to update your fstab and then your crypttab and after that your initramfs.

---


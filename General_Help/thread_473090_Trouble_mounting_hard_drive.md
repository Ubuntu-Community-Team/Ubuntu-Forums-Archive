---
title: "Trouble mounting hard drive"
date: 2007-06-13
forum: General Help
---

### Post by yeago on 2007-06-13
I recently installed Feisty and am having trouble with device /dev/sda1.

/dev/sda exists in fstab, however, /dev/sda1 does not.

What's funny is that fdisk -l lists /dev/sda1 and KNOPPIX mounts the drive and sees its files perfectly fine.

I get errors on startup regarding /dev/sda1

One clue may be that I accidentally installed GRUB to /dev/sda or /dev/sda1 (yes, I know you can't instal grub to a partition, but I may have accidentally).

Problem, one more time: /dev/sda1 doesn't exist and cannot be mounted.

-----------------


My fstab is here
[http://pastebin.co.uk/17021](http://pastebin.co.uk/17021)

Results of fdisk -l /dev/sda are here 
[http://pastebin.co.uk/17023](http://pastebin.co.uk/17023)

Results of dmesg | grep sda are here
[http://pastebin.co.uk/17022](http://pastebin.co.uk/17022)

---

### Post by confused57 on 2007-06-13
Here's an excellent guide for mounting an ext3 partition in fstab, using UUID's:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

If you're able to boot into your Ubuntu install, you could run the "blkid", determine your sda1's UUID, then set up your fstab accordingly...the link explains it pretty well.  You should be able to just copy & paste the UUID from blkid's output into your fstab's sda1 entry.

As an example, your sda1 fstab entry would look something like this:
```
 #/dev/sda1       
UUID=237f0cef-9905-41fb-82ba-bc360fb43a25 /media/datapartition ext3 rw,user  0    1
```

substitute your UUID & mountpoint in the example given.  Also, try using the options in the example rather than what you have.

If you're not able to boot your Ubuntu install, you can use the live cd to mount your root partition & set your fstab up, using UUID:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by yeago on 2007-06-14
> **confused57 said:**
> Here's an excellent guide for mounting an ext3 partition in fstab, using UUID's:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

If you're able to boot into your Ubuntu install, you could run the "blkid", determine your sda1's UUID, then set up your fstab accordingly...the link explains it pretty well.  You should be able to just copy & paste the UUID from blkid's output into your fstab's sda1 entry.

As an example, your sda1 fstab entry would look something like this:
```
 #/dev/sda1       
UUID=237f0cef-9905-41fb-82ba-bc360fb43a25 /media/datapartition ext3 rw,user  0    1
```

substitute your UUID & mountpoint in the example given.  Also, try using the options in the example rather than what you have.

If you're not able to boot your Ubuntu install, you can use the live cd to mount your root partition & set your fstab up, using UUID:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You don't seem to have read my post. Could you try re-reading it?

---

### Post by confused57 on 2007-06-14
I read & reread your initial post and still think it would be worth a try to use UUID in fstab to mount your sda...may not work, it's up to you.

You could do a filesystem check on your sda ext3 filesystem:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

Installing grub IPL to either sda or sda1 shouldn't affect the mounting of your sda1 partition...

Added:  After a google search, I think you may be seeing a bug with the libata_pata drivers?, resulting in your dmesg error message "SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA".
So I don't  think any of my suggestions will help...

---


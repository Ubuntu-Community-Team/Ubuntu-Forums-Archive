---
title: "Changing from ext3 to ext2 - partition is busy"
date: 2008-06-14
forum: General Help
---

### Post by prophet665 on 2008-06-14
I am trying to change my filing system from ext3 to ext2.  The first step is to unmount the partition I want to change.  I sudo over to su and type 

umount /dev/sda1

and I get the following message:

umount: /: device is busy

I am not surprised as this is the main partition that has the OS on it.  Do I need to log in at the console level only?  Won't the harddrive still be in use then?  How do i accomplish this?

Boot from a Live CD?

---

### Post by avtolle on 2008-06-14
As you surmised, boot from a Live CD, whether the Ubuntu one, a Gparted one, or whatever partitioning app fits your fancy.

---

### Post by ModelM on 2008-06-14
I could very well be wrong, but I'm not sure this is necessary. I think you can just mount an ext3 filesystem as ext2 and go from there.

Unless you are concerned about recovering the disk space used by the journal, I'm not sure there's a need to convert.

---

### Post by prophet665 on 2008-06-14
I want to change from ext3 to ext2 for two reasons:

1.  Recovering the journal space
2.  To be able to use the secure delete (srm) command.  Everything I have read has said that a secure delete is impossible with a journaling file system.

The /dev/sda1 partition is auto-mounted at bootup.  Where can I change the boot option for the that partition?  I know these are simple and basic questions, but I am learning a little bit everyday and i am liking this more and more.

Thanks.

---

### Post by ModelM on 2008-06-14
The file you want is /etc/fstab (FileSystemTABle). It contains the instructions, descriptions, etc. for all of the filesystems known to the operating system.

---

### Post by avtolle on 2008-06-14
You are not going to avoid the mounting of /dev/sda1 at bootup, because that's where the operating system is. So, you will need to use the Live CD for formatting purposes, booting from it rather than from the HDD.

---

### Post by prophet665 on 2008-06-14
Here is the output from my fstab table:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0b057e4-81a9-4d02-9e8f-ccf8d226bef0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b4363929-df0b-4fdd-bc3b-934d8d0ca4eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Is it as simple as changing ext3 to ext2 for /dev/sda1 and then rebooting?

That seems WAY too easy.

---

### Post by ModelM on 2008-06-14
Changing the entry to ext2 will, on the next boot, mount the filesystem as ext2, leaving the journal in place & unused.

In order to do the conversion you were originally asking about, though, you cannot boot from the filesystem you want to convert. Boot from another partition, a live cd, a USB stick, or anything else, but you cannot convert an active "live" filesystem. The risk of damage is too great (almost guaranteed) and most tools of this type just won't allow it, anyway.

---

### Post by prophet665 on 2008-06-14
So let me get this straight.  I just change that entry in the fstab file from ext3 to ext2, reboot the machine, and then do the following to recover the journal file:

rm -f .journal

Is this correct?  I will say it again, this seems too easy.

---

### Post by logos34 on 2008-06-14
> **prophet665 said:**
> 
1.  Recovering the journal space
2.  To be able to use the secure delete (srm) command.  Everything I have read has said that a secure delete is impossible with a journaling file system.


what about just using an app like shred or wipe/bcwipe?

Also you can recover disk space by lowering reserved-space (default is 5%)

see man tune2fs

[http://ubuntuforums.org/archive/index.php/t-762352.html](http://ubuntuforums.org/archive/index.php/t-762352.html)

---

### Post by prophet665 on 2008-06-14
When I was looking for secure deletion utilities, I read somewhere that srm was better than shred.  I think it had to do with the method of securely deleting the file.  srm uses a Gutmann pseudo-random overwrites (random ones and zeros) compared with shred's all zeros or all ones overwrite.

Also, any secure deletion program does not work with a journaling file system (hence, the reason i want to move from ext3 to ext2).

I found the link to what made me choose srm over shred:

[http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

---

### Post by ModelM on 2008-06-15
Here's a link which might answer some of your questions...

[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

---

### Post by prophet665 on 2008-06-15
Excellent info!  Wow...there are a couple of steps that I didn't know about and that explained it step-by-step.  Overall, it doesn't seem that hard to do, but the author seems to think changing the root partition is a big, scary deal.  

I guess any time you do something to the root partition it is a big deal.  Since I am of the mindset that if everything goes south, I will just nuke and reload, this time using ext2 instead of ext3.  I will post an update after I have either crashed and burned or successfully moved back.  

Thanks to everyone who has given advice.

Edit:  I am going to guess that I just substitute my own ramdisk for the ones outlined in the following steps:
# mv initrd-2.4.18-26.8.0.img initrd-2.4.18-26.8.0.img.ext3
# mk initrd initrd-2.4.18-26.8.0.img 2.4.18-26.8.0

My ramdisk being initrd-img-2.6.24-18-generic like the following:

# mv initrd-img-2.6.24-18-generic initrd-img-2.6.24-18-generic.ext3
# mk initrd initrd-img-2.6.24-18-generic 2.6.24-18

Does that look correct?

---


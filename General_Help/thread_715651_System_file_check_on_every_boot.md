---
title: "System file check on every boot"
date: 2008-03-05
forum: General Help
---

### Post by Gurth on 2008-03-05
Hello i am pritty new to the Linux platform but over all i am very impressed with.

Have installed ubuntu 7.10 onto my laptop with is running great except for on every boot i go from the splash screen to text and the system performs a file system check.and takes a while to boot.

i have 1 HDD, 1st partition runs windows in fat32, 2 is the ext3 partition and 3 is my swap.

Is there away to stop this happening, i have read on the forums about the tunefs command but the command is unknown in my console.

Thank you Vic

---

### Post by tmcastberg on 2008-03-05
The issues it probably one of two things:

1. You said you have looked into tune2fs, Did you do that before it started checking every time?
Try the following: "tune2fs -c 50 /dev/sda2"
If it's still checking every boot see point 2.

2. You have physical errors on your disk that fsck can't fix (or won't fix automatically).
Do "fsck /dev/sda2" and look for errors.
Post the output here and we'll have a look. :)

---

### Post by Gurth on 2008-03-05
When i type the command tune2fs my console reports no such command so i have not used it ever

fsck /dev/sda2
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

I pressed no just because I'm cautious.

Im pritty new to all this and some of the language is familiar but i dont have a full understanding of what it means.

If im to unmount my fat32 partition will i lose any data stored in that partition or will it just stop ubuntu from seeing the partition? which will then stop ubuntu trying to check the file system for the fat 32?

On boot, the system checks the ubuntu partition and displays [OK]

*It then checks the fat32 partition which is massive and takes ages but then reports [OK]

*this check is what i'm trying to stop because it just takes ages.

I have had this problem before on my other windows based system when i installed a new HDD, It was to do with the way the primary partition was carried out, so i redone the partitioning on this drive with a third party software which sorted it. im not really willing to risk losing any data on my laptop HDD, I could live with it i suppose but ubuntu does boot more slowly than windows which is not right!

Thanks for the feed back

---

### Post by Gurth on 2008-03-05
right i have managed to install the tune2fs command. so now i have done that how do i apply the 'sudo tune2fs -i 1m' command to my /dev/sda1 mount? Will this work?

Right updated

sudo tune2fs -c 50 /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

Thats what is displayed when i try what you said on the sda1 which is my fat32 file system

---

### Post by kpkeerthi on 2008-03-05
Do not run fsck and tune2fs on mounted partitions. In otherwords, boot with a live CD to run those commands.

You will not lose data if you unmount the fat32 partition. 

You can however turn off fsck check on the fat32 partition. To do that, can you post the output of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
```

---

### Post by mcduck on 2008-03-05
Most likely the problem is caused by your /etc/fstab file telling fsck to check your fat32 partition at the same time as root partition.

You can disable that by editing that partitions entry in the fstab file by changing the last number from "1" to "0". ("2" might work as well). "1" tells fsck to checkthat artition first, and it should be used for root partition only. For others you can use either "2" (to check after root) or "0" to disable check for that partition.

Tune2fs will not work, it's only for Ext2/Ext3 partitions.

---

### Post by Gurth on 2008-03-05
Thank you Mcduck your reply worked.

Can i just say that i have installed ubuntu now on two systems, i have tri-booted my media centre pc (the zoom function is great for web surfing on the telly). installed my ati hd3870 with help from here and on my laptop have now solved the little nag i had, all with peoples help from here.

i think its a great operating system, works wonders no matter what spec of system you have, its a little harder to setup some hardware if you have used windows most of your life but with support like this its no big deal.

I hope Microsoft is taking notice.This community is setting the standard

Thanks once again

---


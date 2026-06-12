---
title: "MBR Recovery, i broke hard drive"
date: 2016-04-09
forum: General Help
---

### Post by kacper3 on 2016-04-09
Hi i use this command:
```
sudo dd if=/dev/sda of=/dev/sdb bs=512 count=1
```

After reboot i have errors on grub(cant load SDB) and i cant login to root, only guest. Can i repair this?

**My structure of Ubuntu:**
SDA: /
SDB: /home/

---

### Post by zika on 2016-04-09
You did this on Xenial?
```
if Xenial 
then try chroot
else You're in wrong forum but also try chroot
fi
```
Once in that position either recover part on adb written by command given or (better, much better) save important stuff from sdb first and then try fixing...

---

### Post by kacper3 on 2016-04-09
What is Xenial?

---

### Post by $yl9pAR%t on 2016-04-09
[https://wiki.ubuntu.com/XenialXerus](https://wiki.ubuntu.com/XenialXerus)

---

### Post by kacper3 on 2016-04-09
I using 14.04

---

### Post by howefield on 2016-04-09
Thread moved to the "*General Help*" forum.

---

### Post by oldfred on 2016-04-09
Why were you using dd to copy MBR from sda to sdb?
Always better to just install grub.

 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

      
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kacper3 on 2016-04-09
Logs from boot-info [http://paste.ubuntu.com/15716245/](http://paste.ubuntu.com/15716245/)

---

### Post by oldfred on 2016-04-09
You are showing all sorts of partition table issues on sdb.

It may be possible to repair, but also may just be easier to start over.

You need partition table repairs as logical partitions must be inside the extended partition.
And it looks like partitions are not mounting correctly, may be related to above or you may need fsck to repair each ext4 partition.

       You can possibly repair a MBR partition with fdisk:
sudo fdisk /dev/sdb
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit 

Is/was sdb6 your Linux partition?

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by LostFarmer on 2016-04-09
The 'dd' command you used not only coped the MBR boot code from sda to sdb but also coped the Partition table from sda to sdb.  That seldom is a good thing to do.  The only tool that I have used to recover from a total wrong partition table is 'testdisk'.

---


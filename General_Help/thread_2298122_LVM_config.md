---
title: "LVM config"
date: 2015-10-09
forum: General Help
---

### Post by jimmyh1972 on 2015-10-09
Hi
how can I create a LVM from several hard disks?
never done it before...

---

### Post by nerdtron on 2015-10-09
Well, do have knowledge on LVM itself? The concepts of LVM?

Here are from my notes, just simple explanations

What is LVM?
Logical Volume Management or LVM allow the server to utilize multiple hard drives and combine them to single storage. It allows an easy way to extend or shrink partition depending on how the user needs.
LVM also supports snapshots and cloning for easy backup of system images. LVM is used to allocating disks, striping, mirroring and resizing logical volumes. 
 
LVM Terms
·         Hard Drive &#8211; pertains to physical storage media
·         Physical Volume &#8211; pertains to hard drive partitions assigned to LVM as hard drives
·         Volume Group &#8211; pertains to a group of physical volumes allocated/joined together to become a storage pool.
·         Logical Volume &#8211; pertains to partitions created from the volume group storage pool. These partitions are the one used by the OS and can be dynamically resized.

Then if you want to combine hard drives, here are the steps:

We need to install the LVM packages first in order to use LVM tools
 
[root@server ~]# apt-get install lvm2
 
Now create physical volumes using the command pvcreate.
 
[root@server ~]# pvcreate /dev/sdb1 /dev/sdb2 /dev/sdb3 
 
To verify the newly created physical volumes use the command pvdisplay.
 
[root@server ~]# pvdisplay 
 
Create Volume Groups
Create a new volume group called vg1 using two physical volumes /dev/sdb1 and /dev/sdb2 using the command vgcreate.
 
[root@server ~]# vgcreate vg1 /dev/sdb1 /dev/sdb2
 
To verify the volume group has been created or not use the command vgdisplay.
 
[root@server ~]# vgdisplay 
 
Create Logical Volume
To create logical volume use the command lvcreate. Let us create a logical volume called lv1 with size 200MB.
 
[root@server ~]# lvcreate -L 200M vg1 -n lv1
 
Verify the logical volume is created or not using command lvdisplay.
 
[root@server ~]# lvdisplay 
 
Format and Mount the logical volume
Now format the newly created logical volume and mount it in the /mnt directory or wherever you want.
 
[root@server ~]# mkfs.ext4 /dev/vg1/lv1 
 
And mount the logical volume in the /mnt mount point.
 
[root@server ~]# mount /dev/vg1/lv1 /mnt/
 
Now the logical volume is successfully mounted in /mnt. You can use the new logical volume to store your datas.
 
Extend Volume Group Size
You can extend the Volume Group using vgextend.
 
[root@server mnt]# vgextend vg1 /dev/sdb3 
 
Then resize the logical vloume lv1.
 
[root@server mnt]# lvresize -L +100M /dev/vg1/lv1 
 
Resize the filesystem of logical volume lv1.
 
[root@server mnt]# resize2fs /dev/vg1/lv1 
 
Now verify the new size of the logical volume lv1.
 
[root@server mnt]# lvdisplay /dev/vg1/lv1 


Here is the Official ubuntu link: [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
It is also good to watch youtube videos for LVM

---


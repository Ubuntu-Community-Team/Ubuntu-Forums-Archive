---
title: "disk not showing under blkid"
date: 2016-09-12
forum: General Help
---

### Post by wulfe2 on 2016-09-12
I've searched for this but can't find anything appropriate to my issue.
I created a logical volume with 3 disks (1 x 1TB (sdb), 2x 500GB (sdc & sdd)) and mounted it with no problems.  I added it into fstab and restarted and that worked fine.  On another reboot the system put me into maintenance and going through the log it couldn't mount the logical volume so I removed it from fstab and restarted and got in ok.
When I tried to mount manually it failed, couldn't find it.  lvdisplay shows the logical volume but shows it as not available.
If I use lsblk I can see the drive fine.
```
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 279.5G  0 disk 
&#9500;&#9472;sda1                  8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9492;&#9472;sda5                  8:5    0   279G  0 part 
  &#9500;&#9472;ubuntu--vg-root   252:0    0   277G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 252:1    0     2G  0 lvm  [SWAP]
sdb                     8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                  8:17   0 931.5G  0 part 
sdc                     8:32   0 465.8G  0 disk 
sdd                     8:48   0 465.8G  0 disk 
```

When I use blkid it doesn't appear at all.
```
/dev/sda1: UUID="42b8ee96-83d9-4052-a724-ea7179169653" TYPE="ext2" PARTUUID="3acaf9a2-01"
/dev/sda5: UUID="iehhBk-vlLM-AVLv-x25p-f4Fx-i2c8-WfjLB0" TYPE="LVM2_member" PARTUUID="3acaf9a2-05"
/dev/sdb1: UUID="ejKfq1-i893-gni7-IOFs-1sM9-A7Qc-9j0ncH" TYPE="LVM2_member" PARTUUID="7b49d14b-01"
/dev/sdc: UUID="2rIm9V-KlE8-TbWs-ZFYL-fdr8-efMe-5kJFUh" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="af53f0e4-06f6-4d1f-b9c6-b8a7bd6ce67e" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="7c30fb71-26a8-463f-8ef9-b5e5f2df5423" TYPE="swap"
```

Anybody have any ideas to fix this?

Thanks

---

### Post by wulfe2 on 2016-09-12
So I found a good article on restoring the logical volume at [https://www.jethrocarr.com/2013/11/23/restoring-lvm-volumes/](https://www.jethrocarr.com/2013/11/23/restoring-lvm-volumes/).  Worked great although the archive file was from before it was fully created so I lost the data.  Fortunately I still had another backup of that.  I think I'll keep that copy for a little while just in case.

---


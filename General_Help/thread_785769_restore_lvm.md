---
title: "restore lvm"
date: 2008-05-07
forum: General Help
---

### Post by go_dragons on 2008-05-07
I have been a full-time user of ubuntu since the days of dapper, and have loved every minute of it. Recently I think my curiosity got the best of me and I decided that I wanted to try out arch linux. That is when the problem began...but I hope you won't hold that against me!

On my system I have two 250GB hard drives. The first hard drive has a 100MB boot partition, a 10GB root partition, a 4GB swap, and the rest is allocated for lvm. The second hard drive is is used completely for lvm.

Pertaining to LVM, I have my two physical devices, sda4 and sdb. Since I was using the lvm partition for my home drive, there is one volume group called home_vg and there is one logical volume called home formatted with the jfs filesystem.

As I installed arch linux, I decided stupidly to overwrite my ubuntu system rather than dual boot. The install went without a hitch, though I did not bother with the lvm partitions until after the install was complete. When the system was installed I ran lvscan under arch and found that my lvm partitions were there and all the data was available. I added the home logicalvolume to /etc/fstab and set it to mount on /home. After rebooting arch it still mounted fine and when I created my users they were able to use the old home directories...everything is great, right?

I thought so too, but after several reboots and changing of configuration files that to my knowledge are unrelated, my home directory refused to mount. At this point I switched to my ubuntu live CD and installed lvm2 on the liveCD environment. lvscan showed my logical volume just as they are supposed to but it still refused to mount. I dont remember the exact error but it was something to the effect of 'possible wrong filesystem or bad superblock' 

I decided it was time to look into restoring my lvm data. A quick search on google returned [this site]("http://codeworks.gnomedia.com/archives/2005/general/lvm_recovery/")
which I used for reference.

since I had overwritten my old ubuntu partition I did not have an lvm backup, so I ran vgcfgbackup now to obtain a current backup.(hopefully that is not my problem :S) after that I followed the instructions on the page:

```

ubuntu@ubuntu:~$ sudo pvremove -ff /dev/sdb
Really WIPE LABELS from physical volume "/dev/sdb" of volume group "home_vg" [y/n]? y
  WARNING: Wiping physical volume label from /dev/sdb of volume group "home_vg"
  Labels on physical volume "/dev/sdb" successfully wiped
ubuntu@ubuntu:~$ sudo pvremove -ff /dev/sda4
  Couldn't find device with uuid 'PRfUlr-HYT0-J7Mn-1CnE-LnkS-KSMt-Lw7s5M'.
  Couldn't find all physical volumes for volume group home_vg.
  Couldn't find device with uuid 'PRfUlr-HYT0-J7Mn-1CnE-LnkS-KSMt-Lw7s5M'.
  Couldn't find all physical volumes for volume group home_vg.
  get_pv_from_vg_by_id: vg_read failed to read VG home_vg
  Labels on physical volume "/dev/sda4" successfully wiped

```
afterwhich pvscan lvscan and vgscan returned nothing. I rebooted the (still in ubuntu live CD) and installed lvm2 again just in case anything needed to be refreshed.
```

sudo pvcreate -u L2ljei-oHMC-8gia-Twnw-RQPx-piNd-s6n35h /dev/sda4
sudo pvcreate -u PRfUlr-HYT0-J7Mn-1CnE-LnkS-KSMt-Lw7s5M /dev/sdb
sudo vgcreate -v home_vg /dev/sda4 /dev/sdb
vgcfgrestore -f /etc/lvm/backup/home_vg home_vg

```
that last line is using the backup that I created earlier.
```
vgchange -a y home_vg
```
to activate the group.


This is where my help ends, but I still have problems. pvscan and vgscan return just like they are supposed to. lvscan does not return anything. I am afraid to run lvcreate because I do not want to lose the data on my volume. Sadly I do not have any backups for my data so I know I will get scolded for that. Belive me, I will backup my data in the future to avoid this problem! Please, if there is anyone out there that can tell me how to reconstruct my logical volumes without destroying my data, I would GREATLY appreciate it!

Thanks in advance for any advice I can get, I know I can count on support from the ubuntu community. I have attached a copy of my vgcfgbackup file.

---

### Post by Zburatorul on 2008-10-06
Hi,

I have a somewhat similar problem. 
I have a RAID1 array with 2 disks under **/dev/md0**. *The device has 3 lvm logical volumes on it. The last one is for lvm snapshots.*
For a while I haven't used the RAID at all, as I've been away from the computer. I moved the array to a new computer and tried adding it to the system.

Unfortunately, in a hurry, and not knowing what I was doing, I ran
```
sudo pvcreate -v /dev/md0
    Set up physical volume for "/dev/md0" with 488396928 available sectors
    Zeroing start of device /dev/md0
  Physical volume "/dev/md0" successfully created
```

Is there a way for me to recover the lvm partition table on that device?
The device wasn't part of any volume group yet, and therefore I have no backup file for it under /etc/lvm/backup.

Any help, even on a better formulation of the question or problem, would be much appreciated.

---


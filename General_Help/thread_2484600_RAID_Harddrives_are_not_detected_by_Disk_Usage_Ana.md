---
title: "RAID Harddrives are not detected by Disk Usage Analyzer but appear in the lsblk list"
date: 2023-03-03
forum: General Help
---

### Post by vilthivus on 2023-03-03
My workstation that comes with Ubuntu 20.04 Desktop pre-installed has two HDD's installed by someone else (not me). The two HDD's are listed by the lsblk, which are shown as
```

sda           8:0    0   3.7T  0 disk  
&#9492;&#9472;md0         9:0    0   3.7T  0 raid1 /data
sdb           8:16   0   3.7T  0 disk  
&#9492;&#9472;md0         9:0    0   3.7T  0 raid1 /data

```
They also appear under /dev as sda and sdb, and can run hdparm on them. But they don't appear anywhere in the Files and Disk Usage Analyzer does not detect them either. 

The HDD's was configured with the RAID on. I need to access these disks because I plan on using them for backups.

---

### Post by #&amp;thj^% on 2023-03-03
it may help to go into BIOS setup, find the setting for SATA/SSD Controller, and either disable it or change from RAID to AHCI.

---

### Post by vilthivus on 2023-03-03
I have seen this solution somewhere else, the reason I hesitate to try that is that this workstation I am working on is my lab's and there must be a reason why my colleague chose to use RAID. May be he is more familiar with it that troubleshooting any problem later on will be easier and so on.
So, it seems like Ubuntu is not well suited with RAID HDD. I hope I am wrong.

---

### Post by MAFoElffen on 2023-03-03
Stop please... They are showing as mdadm md devices, which is mdadm software RAID.

First-- Please post the output of 
```

sudo mdadm --examine /dev/sd[a-b]
sudo mdadm --detail --scan
grep . /proc/mdstat

```

---

### Post by #&amp;thj^% on 2023-03-03
> **MAFoElffen said:**
> Stop please... They are showing as mdadm md devices, which is mdadm software RAID.

First-- Please post the output of 
```

sudo mdadm --examine /dev/sd[a-b]
sudo mdadm --detail --scan
grep . /proc/mdstat

```
Yep my bad, good catch.
I flat just blew right by that...

---

### Post by MAFoElffen on 2023-03-03
No problems. We are each others best backup. I need another set of eyes sometimes. LOL

---

### Post by #&amp;thj^% on 2023-03-03
> **MAFoElffen said:**
> No problems. We are each others best backup. I need another set of eyes sometimes. LOL

;)
I'm just happy the poster was smarter than me...LOL

---

### Post by vilthivus on 2023-03-03
sudo mdadm --examine /dev/sd[a-b]```
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 1228e719:1edd9ac3:a432ad2c:796b77af
           Name : musaka:0  (local to host musaka)
  Creation Time : Thu Mar  2 16:01:29 2023
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 7813772976 (3725.90 GiB 4000.65 GB)
     Array Size : 3906886464 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 7813772928 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=48 sectors
          State : clean
    Device UUID : 3f5eb0ee:0188cb26:4f2a45ce:f59e880a

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Mar  3 17:36:55 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : a26f5c95 - correct
         Events : 22340


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 1228e719:1edd9ac3:a432ad2c:796b77af
           Name : musaka:0  (local to host musaka)
  Creation Time : Thu Mar  2 16:01:29 2023
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 7813772976 (3725.90 GiB 4000.65 GB)
     Array Size : 3906886464 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 7813772928 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=48 sectors
          State : clean
    Device UUID : 5c648766:49dac9cd:1a1ce374:5e6dfbe5

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Mar  3 17:36:55 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 43557530 - correct
         Events : 22340


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

sudo mdadm --detail --scan
```

ARRAY /dev/md0 metadata=1.2 name=musaka:0 UUID=1228e719:1edd9ac3:a432ad2c:796b77af

```

grep . /proc/mdstat
```

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb[1] sda[0]
      3906886464 blocks super 1.2 [2/2] [UU]
      bitmap: 2/30 pages [8KB], 65536KB chunk
unused devices: <none>

```

---

### Post by vilthivus on 2023-03-03
I just realized that the HDD is accessible under /data. The /data is the HDD itself, running df -h shows that /data has a size of 3.7 T which is the size of the HDD.
I don't know if that's a sign that it works. But the fact that it doesn't show up in the Disk Usage Analyzer still worries me.

---

### Post by MAFoElffen on 2023-03-03
So /dev/md0 is an mdadm RAID1 member, and shows in your lsblk output as mounted as '/data'... If you post the contents of your '/etc/fstab' file, you will most likely see that it is mounted at boot from there.

Do:
```

ls -ltr /data

```
And post the output... To see who it is owned by (User:Group). once ownership and permissions are worked out, you should be able to create a folder on that storage, and point your backups to that folder.

---

### Post by #&amp;thj^% on 2023-03-04
Courtesy bump for the OP, this is something that needs an answer.

---

### Post by vilthivus on 2023-03-04
I am sorry I cannot try that at the moment, my office is locked. Will be back again on Monday.
For now, I will only say that I can create a file under /data.

---

### Post by #&amp;thj^% on 2023-03-04
Good News, and Thanks for the updated info.
see you Monday then...

---

### Post by MAFoElffen on 2023-03-04
> **vilthivus said:**
> I am sorry I cannot try that at the moment, my office is locked. Will be back again on Monday.
For now, I will only say that I can create a file under /data.
I would check the access/permissions first... Then create a folder for your backups. Who knows, in the future, you may want to put other things there (in that storage) also. Easy to keep things organized from the start, right?

That way everything has a place, and you know where to go to find things.

---

### Post by vilthivus on 2023-03-06
Hi thanks for holding on, here's the output of ls -ltr /data
```
total 16
drwx------ 2 root root 16384 Mar  2 16:04 lost+found

```

---

### Post by #&amp;thj^% on 2023-03-06
Are you going to be the only one accessing that drive?

---

### Post by vilthivus on 2023-03-06
No, my supervisor says he's also going to need to access the drive occasionally.
These extra drives will be used for backup, the root and home are located in another storage (an SSD).

---

### Post by MAFoElffen on 2023-03-06
Create a group that both of you are going to be members of, such as 'backupteam'
```

sudo groupadd backupteam
sudo usermod -a -G backupteam Your_UserID

```
Substituting your username for Your_UserID, then add your Bosses Username to that group also...

Then do
```

chown Your_UserID:backupteam /data
chmod 770 /data

```
That should give you and members of that group read/write/execute permissions to that folder.

---

### Post by #&amp;thj^% on 2023-03-06
Ninjed LOL
Great minds think a like.
not to confuse the OP mine is very close:
You need to change the owner and / or permissions of the mount.

Changing the owner of a mount to a particular user is definitely not a good idea for shared computers. It is better to assign read and write permissions to a group to which all the users belong.

For example, if users is the group to which all the regular users belong, something like this may work better:
```

sudo chown root:users /to-your-mountpoint
```

Then this command will change the permissions to edit and delete files:
```
sudo chmod g+rw /again-your/mount-point
```

---

### Post by MAFoElffen on 2023-03-06
LOL. Yup. 

As an Administartor, later you can recheck the members of that group doing this:
```

sudo grep 'backupteam' /etc/group

```

---

### Post by MAFoElffen on 2023-03-06
An after-thought... That is 4TB of secure mirrored storage. Like I said before, you could create a folder underneath /data for your backups, then set that folder's ownership and permissions. That way, if the company later wants to store other things, for shared storage, there is a place to grow / migrate to.

That way, if you later create another folder, with access and to be shared for other people, you can do that.

As an IT Consultant for years, those are the kinds of things I think of with planning for business decisions.

---


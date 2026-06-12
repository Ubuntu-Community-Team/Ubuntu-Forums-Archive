---
title: "Cannot show mounted harddrive due to bug in Disk Manager"
date: 2015-02-26
forum: General Help
---

### Post by JoeDaddy on 2015-02-26
Ubuntu 14.04
In order to have my additional hard drive mount at boot up I have to set up the  Disk utility- mount options - correctly. Due to a bug, I am told that  the box "Show in User Interface" must be UNchecked.  That works but then  I can not see my mounted drive anywhere.  I tried a fix to show mounted  drives on the desktop but because of the unchecked box this drive will  not show up although any other mounted drive does. I want to have a place where I can "see" my automatically mounted hard  drive so I can add and delete files at will.  Can you tell me how to get an icon on the desktop for that drive?   /dev/sdb1 Thanks!

---

### Post by ajgreeny on 2015-02-26
It will probably be easier to add a line to /etc/fstab to mount the partition at boot; certainly it will be easier for me as I can't help with the various options in Disks.

Tell us all you can about the drive and show us the output of ```
sudo parted -l
sudo blkid -c /dev/null
```and we can tell you what to add.

---

### Post by JoeDaddy on 2015-02-26
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   46.6GB  46.5GB  primary   ntfs
 3      46.6GB  80.0GB  33.4GB  extended
 5      46.6GB  77.9GB  31.3GB  logical   ext4
 6      77.9GB  80.0GB  2136MB  logical   linux-swap(v1)
[SIZE=4]
It's this drive[/SIZE]
[SIZE=4]**Model: ATA ST3160318AS (scsi)**[/SIZE]
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  105GB  105GB   primary  ext4
 2      105GB   160GB  55.2GB  primary  ntfs

jq@jq-Dell-DV051:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="System Reserved" UUID="5EF2983BF298197B" TYPE="ntfs" 
/dev/sda2: UUID="56489B99489B7709" TYPE="ntfs" 
/dev/sda5: UUID="f2f6823e-34d0-4f0c-b1d9-1b76da7358bc" TYPE="ext4" 
/dev/sda6: UUID="092b6022-cad7-4782-8e4d-4ae3df8d2896" TYPE="swap" 
/dev/sdb1: LABEL="105G" UUID="6527a416-82a7-4d86-8425-6feef408d3bc" TYPE="ext4" 
/dev/sdb2: LABEL="55G" UUID="0AA3E74D17C07CC7" TYPE="ntfs" 
[B]
It's the 105G that will not show up[/B].

---

### Post by CaptainMark on 2015-02-26
```
sudo mkdir /media/ntfs_filesystem
sudo echo "UUID=0AA3E74D17C07CC7 /media/ntfs_filesystem ntfs defaults 0 2" >> /etc/fstab
```This will add the drive to your fstab and mount it at boot, you can replace ntfs_filesystem with whatever name you want the drive to show as, or change the path altogether if you want to mount it somewhere else, use sudo mount -a to mount it straight away without a reboot

---

### Post by JoeDaddy on 2015-02-26
Starting over because the drive was mounted but I was not able to view it.  I set it so it is unmounted but can be viewed, which is what I assume I need as a beginning.  Secondly the drive was the ext4 that I want to mount at bootup.  Here are the otuputs of the previous commands.  I'll only give you the results for the drive I want to mount:

Model: ATA ST3160318AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  105GB  105GB   primary  ext4
 2      105GB   160GB  55.2GB  primary  ntfs


/dev/sdb1: LABEL="105G" UUID="6527a416-82a7-4d86-8425-6feef408d3bc" TYPE="ext4"

So how do I modify this to cover the above drive?
sudo mkdir /media/ntfs_filesystem
sudo echo "UUID=0AA3E74D17C07CC7 /media/ntfs_filesystem ntfs defaults 0 2" >> /etc/fstab


I tried the following but got Permission Denied!
jq@jq-Dell-DV051:~$ sudo mkdir /media/ext4_filesystem
jq@jq-Dell-DV051:~$ sudo echo "UUID=6527a416-82a7-4d86-8425-6feef408d3bc /media/ext4_filesystem ext4 defaults 0 2" >> /etc/fstab
bash: /etc/fstab: Permission denied

---

### Post by ajgreeny on 2015-02-26
What about the ext4 partition; do you want that mounted at boot and available, as well as the ntfs one?

---

### Post by JoeDaddy on 2015-02-26
The ext4 is the one I want to mount at bootup.  I do not need to have the ntfs one.

---

### Post by ajgreeny on 2015-02-26
OK, I will be back tomorrow with a different line to add for the ext4 partition.  I am.using android tablet at the moment and I find it imposssible to copy/paste with it, so till tomorrow, unless an answer appears before I get back again.

---

### Post by ajgreeny on 2015-02-27
You will need to add the lines below to your /etc/fstab file in order to mount the partition at boot, but back up fstab first, just in case something goes wrong, with command ```
sudo cp /etc/fstab /etc/fstabbackup
``` You will also need to change the ownership of the newly made mountpoint folder to you so that you can both read and write to it as user.

First make the folder for the mountpoint that will mean something to you, eg, if it is a data storage partition you can call it /media/data
```
sudo mkdir /media/data
```You will then need to change ownership of that mountpoint folder to you with command```
sudo chown -R jq:jq /media/data
```assuming you are still using jq as your username.  I show this as a recursive command as I assume there are already files and folders in the partition, all of which must belong to you.
Now edit fstab as root with ```
sudo -H gedit /etc/fstab
``` and add these two lines.
```
# data partition was /dev/sdb1 after manual addition.
UUID=6527a416-82a7-4d86-8425-6feef408d3bc /media/data           ext4    defaults        0       2
```
Finally check that all is OK with ```
sudo mount -a
```If no error shows, the partition will now be mounted, and you should be able to read from it and write to it as user without a problem.

---

### Post by JoeDaddy on 2015-02-27
**Solved**
:p  Works perfectly.  Where do you learn all of that? Is there a book?

---

### Post by ajgreeny on 2015-02-27
No, it is 10 years of using Ubuntu that has allowed me to know things that are not obvious to new users.
Please mark the thread as solved from.Thread tools menu at the top.

---


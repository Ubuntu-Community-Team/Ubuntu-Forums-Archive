---
title: "mount /dev/loop1 /mnt/   ext3"
date: 2015-04-25
forum: General Help
---

### Post by ELMIT on 2015-04-25
We got a backup from Domainfactory.de with a README file to do folowing:

losetup /dev/loop0 name_of_disk_file
mount /dev/loop0 /mnt
... Files are in directory /mnt ...
umount /mnt
losetup -d /dev/loop0


So we tried above:

sudo mkdir /mnt/Jiffy-54321
sudo losetup /dev/loop1 /mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_54321.raw
sudo mount -text3 /dev/loop1 /mnt/Jiffy-54321

mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail
[815963.220907] EXT4-fs (loop1): unable to read superblock
[816251.076192] EXT4-fs (loop1): VFS: Can't find ext4 filesystem


What is wrong?

---

### Post by dino99 on 2015-04-25
i'm not used with /dev/loop? but here is what the manpage says   [http://manpages.ubuntu.com/manpages/raring/man8/losetup.8.html](http://manpages.ubuntu.com/manpages/raring/man8/losetup.8.html)

---

### Post by ELMIT on 2015-04-25
I think the key is in:

dmesg | tail
[815963.220907] EXT4-fs (loop1): unable to read superblock
[816251.076192] EXT4-fs (loop1): VFS: Can't find ext4 filesystem



the mount command was:

sudo mount -text3 /dev/loop1 /mnt/Jiffy-54321

but 

dmesg | tail
[815963.220907] EXT4-fs (loop1): unable to read superblock
[816251.076192] EXT4-fs (loop1): VFS: Can't find ext4 filesystem


Why it wants to mount EXT4 when I specify EXT3 ????

---

### Post by Holger_Gehrke on 2015-04-25
Try to identify the contents of the file by running 'file /mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_54321.raw'. Ext4 is an extension of ext3 is an extension of ext2. If mount fails at something as basic as finding the superblock, it doesn't get to the point where the differences between 3 and 4 are important.

Edit: Shouldn't there be a space between '-t' and 'ext3' ? At least according to 'man mount' it should ...

---

### Post by steeldriver on 2015-04-25
iirc you may need to identify the start of the partition (using parted or fdisk) and pass the byte offset to losetup using the -o parameter

---

### Post by ELMIT on 2015-04-26
file jiffybox_j12345_disk_54321.raw
jiffybox_j12345_disk_54321.raw: sticky writable, regular file, no read permission


I got new instructions to mount, with the remark, on our system it works - for me it doesn't:

sudo mount -o loop jiffybox_j12345_disk_54321.raw /mnt/Jiffy-54321
mount: you must specify the filesystem type


dmesg |tail
[815963.220907] EXT4-fs (loop1): unable to read superblock
[816251.076192] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[816319.931359] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[852313.128269] EXT4-fs (loop0): VFS: Can't find ext4 filesystem
[852313.128313] EXT4-fs (loop0): VFS: Can't find ext4 filesystem
[852313.128332] EXT4-fs (loop0): VFS: Can't find ext4 filesystem
[852313.128368] FAT-fs (loop0): invalid media value (0x00)
[852313.128369] FAT-fs (loop0): Can't find a valid FAT filesystem

---

### Post by Holger_Gehrke on 2015-04-26
> **ELMIT said:**
> file jiffybox_j12345_disk_54321.raw
jiffybox_j12345_disk_54321.raw: sticky writable, regular file, no read permission

Try that again but with 'sudo' so 'file' can read the contents and identify them.

> **ELMIT said:**
> 
I got new instructions to mount, with the remark, on our system it works - for me it doesn't:

sudo mount -o loop jiffybox_j12345_disk_54321.raw /mnt/Jiffy-54321
mount: you must specify the filesystem type


That's just a short version of the original instructions; all it does differently is that it doesn't explicitly set up a loop device, but leaves it to mount to set it up and it leaves out the file system type and leaves mount to figure it out for itself ...

---

### Post by ELMIT on 2015-04-26
sudo file jiffybox_j12345_disk_54321.raw
jiffybox_j12345_disk_54321.raw: sticky data

I thought so, that both variants are the same, but gave it a shot.

---

### Post by ELMIT on 2015-04-29
I tried to untar the files by clicking on the *tar.gz icon, ... which gave me a file of 22 GB and the notice that it is finished.
I tried then to use tar -xvzf   and got a 50 GB file, ... THAT one worked then to mount.


Now I get the next problem:
This backup includes web sites with mysql

How can I try to get the mysql data into my current installed mysql system?

I found in the backup directory /var/lib/mysql/<database>/    *MYD  *MYI  *.frm files

I found hints, that the backup used   mysql-server-5.5.* files   which my system also has. Assuming I might use the same mysql version.

I cannot just replace the directory /var/lib/mysql with the old one, because I have already started new databases.

---

### Post by SeijiSensei on 2015-04-29
Is this an ISO image?  What if you try:
```
sudo mount -o loop -t iso9660 jiffybox_j12345_disk_54321.raw /mnt/Jiffy-54321
```
What do you see if you run "file jiffybox_j12345_disk_54321.raw"?

---

### Post by ELMIT on 2015-04-29
It is now working!
The problem was that the file was not uncompressed completely. GUI untar gave me a 22 GB file and said finished. The command line gave me 50 GB !!!! This one I can now mount!!!

I tag this thread as solved and open a  new one for my mysql question.

---

### Post by btindie on 2015-04-29
> **ELMIT said:**
> 
I cannot just replace the directory /var/lib/mysql with the old one, because I have already started new databases.

Making sure your own MySQL instance is shutdown, you could try bind mounting the restored /var/lib/mysql directory on top of your own one - nothing will happen to the contents.
```
sudo mount --bind [COLOR=#000000]/mnt/Jiffy-54321/var/lib/mysql /var/lib/mysql[/COLOR]
```[COLOR=#000000]
you can then start up MySQL and you should be able to access the DB. Just unmount the bind mount to get your own directory back after previously shutting down MySQL.[/COLOR]

---


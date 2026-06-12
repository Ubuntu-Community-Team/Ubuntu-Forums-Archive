---
title: "Error Mounting Message /dev/sdb at /media..."
date: 2018-03-11
forum: General Help
---

### Post by allosaurus66 on 2018-03-11
Ubuntu 17.10

Hello everyone, thanks in advance for any help.

The system opens fine, but when I click on the hard drive 1TB location I get a window message: 

Can't access location
Error mounting /dev/sdb at /media/this-is-my-user/1TB: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb" "/media/this-is-my-username/1TB"' exited with non-zero status 32: mount: /media/this-is-my-user/1TB: can't read superblock on /dev/sdb

I can't copy paste the message so I gess all this double (triple) quotes are right.

System is brand new, but after copying data from an external drive to the TeraByte (TB) I guess something went wrong and after booting I could not get the TB partition any more.

I would very much appreciate some help.
Thanks very much.

---

### Post by Bashing-om on 2018-03-11
allosaurus66; Hummmm ...

Well, we know we have to run some kind of file system check/repair:
> 
 mount: /media/this-is-my-user/1TB: can't read superblock on /dev/sdb


so let's see if we can find out what we are working with.
Post back - Between Code Tags - the output of terminal commands:
```

sudo parted -l
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending what shows ->

[INDENT]is what we do next
[/INDENT]

---

### Post by Yellow Pasque on 2018-03-11
> Error mounting /dev/sdb

It should be /dev/sdb1 (or sdb2, etc). I don't know why the GUI would try to mount it like that. Maybe output of the commands Bashing-om suggested will give us a clue.

---

### Post by allosaurus66 on 2018-03-12
[FONT=courier new]Many thanks for your interest Bashing-om, 

the command mount, with my proper user name: 

[/FONT][FONT=courier new]```

mount: /media/this-is-my-user/1TB: can't read superblock on /dev/sdb
 
```[/FONT][FONT=courier new]

gives me an arrow like: 
> 
[FONT=courier new][FONT=arial black]
[/FONT][/FONT]
for which I am too newbie to continue.


After [FONT=arial black]

```
[B]
sudo parted -l
[/B]
```
[/FONT][/FONT]
[FONT=courier new][FONT=arial black]

I get:[/FONT][/FONT]

```

Modelo: ATA KINGSTON SA400S3 (scsi)
Disco /dev/sda: 240GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: gpt
Disk Flags: 

Numero  Inicio  Fin    Tamaño  Sistema de archivos  Nombre                Banderas
 1      1049kB  538MB  537MB   fat32                EFI System Partition  arranque, esp
 2      538MB   240GB  240GB   ext4


Modelo: ATA ST1000DM010-2EP1 (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones: loop
Disk Flags: 

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   1000GB  1000GB  ext4


```

Also the
```

**cat /etc/fstab**

```

gives me this: 

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5d633fae-92ff-48d8-a17f-624ff459fd48 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8651-E876  /boot/efi       vfat    umask=0077      0       1
/swapfile  


```

---

### Post by Bashing-om on 2018-03-12
allosaurus66; Welp -

Not totally unexpected results -

Before we proceed with the file system check and the attempted repair .. are you sure you are happy to devote ONE TB to a single partition ?

See then what results:
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting) <- Basic filesystem checks and repairs

#-> From liveUSB/DVD <- so everything is unmounted,swap off if necessary, 

#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sdb1

```
#if errors; which I do expect !  -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sdb1

```
fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

Here if it errors out, post that output ! As it:
Remains a possibility/probability that we will have to lend a hand manually and replace the superblock from backups.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by allosaurus66 on 2018-03-12
Thx,
Before I ran the checks, would you have a a TB in more than one partition?

---

### Post by SeijiSensei on 2018-03-12
Shouldn't you be trying to mount /dev/sdb1, not the device /dev/sdb.

---

### Post by oldfred on 2018-03-12
I think you formatted drive, and did not even create sdb1 partition.

```
Modelo: ATA ST1000DM010-2EP1 (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones: [COLOR=#ff0000]loop[/COLOR]
```

Should be gpt or dos/msdos/MBR type partitioning.

---

### Post by allosaurus66 on 2018-03-12
I explained wrong from the beginning. Sorry my tech language. I have 2 hard drives one is 250 GB the other is 1TB. I said partition wrongly.

---

### Post by Bashing-om on 2018-03-13
allosaurus66; Hey - hey

Your 'parted -l' output:
> 
Tabla de particiones: [color=red]loop[/color]


where we expect something like my output:
> 
sysop@x1604:/$ sudo parted -l
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: [color=green]msdos[/color]
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  149GB  149GB   primary   ext4            boot
 2      149GB   165GB  15.7GB  extended
 5      149GB   154GB  4719MB  logical   linux-swap(v1)



We propose that you do not have any partitions on that 1TB drive . While one can do that ,, it IS NOT a good practice, and will lead to serious addressing issues . How about at this point partitioning that drive in a useful format ?

[INDENT][INDENT]just my thought on the natter
[/INDENT][/INDENT]

---

### Post by allosaurus66 on 2018-03-14
OK for me, we can do that, but first I would like to just being able to access the TB, pick up some files to make a back up of them, and then proceed to the partitioning of the tera.

Cheers!

---

### Post by oldfred on 2018-03-14
It may look like a very large or Superfloppy drive.
What format is it?

Example with FAT32
 mount superfloppy fat formatted.
mount -t vfat /dev/sdb /media/disk/

You may have to make the mount point /media/disk if using example.

---

### Post by allosaurus66 on 2018-03-16
Thanks for your interest.


Due to being stuck for a couple of days I opted for re-installing Ubuntu. This time the Ubuntu 16, in English
No problem with the installation. 
I can see the icon of my 1TB hard drive on my left hand side of the  desktop. I click on it and nothing happens, so I go to files folder, I  can see the TB there, i click on it and I get:

Error mounting /dev/sdb at /media/aelm/1TB: Command-line `mount -t  "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb" "/media/aelm/1TB"'  exited with non-zero exit status 32: mount: /dev/sdb: can't read  superblock

 I wrote:

sudo mount -t vfat /dev/sdb /media/disk/

I got this:
mount: mount point /media/disk/ does not exist

Cheers.

---

### Post by SeijiSensei on 2018-03-17
First, I suggest you boot into the "Try Ubuntu" mode and run gparted from there to create a Linux partition on the disk.  It will be called /dev/sdb1.  Then you'll need to create the mount point as root with sudo and mount the partition there.
```

sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

```
For some reason, despite my earlier posting, you persist in trying to mount /dev/sdb.  Create a partition that spans the entire drive and mount that instead.

---

### Post by Yellow Pasque on 2018-03-17
> First, I suggest you boot into the "Try Ubuntu" mode and run gparted from there to create a Linux partition on the disk.

The OP wants to recover some data before repartitioning/reformatting.

> For some reason, despite my earlier posting, you persist in trying to mount /dev/sdb.

/dev/sdb may be correct if it's a whole disk partition with no partition table. fdisk is showing a "loop" partition table ("Tabla de particiones: loop"). 
**OR** fdisk can't find the partition table because it's corrupted/missing. (This is what I would guess.) In that case, something like testdisk may be useful: [https://www.linux.com/learn/how-fix-mangled-partition-table-linux](https://www.linux.com/learn/how-fix-mangled-partition-table-linux)

---

### Post by allosaurus66 on 2018-03-17
[B] 
@Bashing-om, I am getting the [COLOR=#ff0000]partition table msdos[/COLOR] like you posted earlier.

The cat /etc/fstab gives me this:
[/B]
> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a2b8f9d7-b75e-4fb2-8c1b-c5abaf35d9c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2a39adc2-0909-4353-9dc1-89d1a615b7fe none            swap    sw


[B]
And the sudo parted -l[/B]

> 

Model: ATA KINGSTON SA400S3 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
[COLOR=#ff0000]**Partition Table: msdos**[/COLOR]
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  223GB  223GB   primary   ext4            boot
 2      223GB   240GB  17,1GB  extended
 5      223GB   240GB  17,1GB  logical   linux-swap(v1)


Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0,00B  1000GB  1000GB  ext4



What next?

---

### Post by allosaurus66 on 2018-03-17
@SeijiSensei
If I do this you suggest

sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

, the data in the disk, will it be erased?

---

### Post by allosaurus66 on 2018-03-18
I got this also:

```
[FONT=Liberation Mono][SIZE=2]aelm@aelm-MS-7A70:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1[/SIZE][/FONT]
[FONT=Liberation Mono][SIZE=2]e2fsck: No such file or directory while trying to open /dev/sdb1[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]Possibly non-existent device?[/SIZE][/FONT][FONT=Liberation Mono][SIZE=2]
[/SIZE][/FONT]
```[FONT=Liberation Mono][SIZE=2]

And this:

```

aelm@aelm-MS-7A70:~$ sudo e2fsck -C0 -p -f -v /dev/sdb
/dev/sdb has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!

```


Thanks again.


[/SIZE][/FONT]

---

### Post by allosaurus66 on 2018-03-18
> **SeijiSensei said:**
> First, I suggest you boot into the "Try Ubuntu" mode and run gparted from there to create a Linux partition on the disk.  It will be called /dev/sdb1.  Then you'll need to create the mount point as root with sudo and mount the partition there.


is this done with the resize/move menu, in g parted?

---

### Post by SeijiSensei on 2018-03-18
No, you need to point to the empty drive and run "Create Partition Table" followed by New.  

However you will lose the data on the drive if you reformat.  I don't have any suggestions about how to deal with that other than suggesting tools like [testdisk]("https://www.cgsecurity.org/wiki/TestDisk") and [photorec]("https://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by Yellow Pasque on 2018-03-18
> **allosaurus66 said:**
> I am getting the partition table msdos

No. You're looking at the wrong disk. Please see the link I gave in my last post.

---

### Post by allosaurus66 on 2018-03-23
Hi all, thanks again for being there and help me out.


After some commands, the disks utility and also gparted, I managed to mount  the TeraByte disk by erasing everything inside and creating a new partition; 

Now I can access it from my desktop, also from the Launchpad, but  when I try to put files in it by dragging them inside the just bounce  back out. I guess something is not yet complete of this whole process.  Permissions, maybe?

If I right click inside it, at the permissions tab, it says I am not the owner. The owner is root. 

1- So, what can I do to be able to use it without being root all the time. My idea is to use it as I use my home folder: putting files in and out of  it with ease. 

2- Is it a good place (or the best place) the mount point as it is or is better to mount it somewhere else?


I have this:
> 

Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  223GB  223GB   primary   ext4            boot
 2      223GB   240GB  17,1GB  extended
 5      223GB   240GB  17,1GB  logical   linux-swap(v1)


Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4



> 
aelm@aelm-MS-7A70:~$ findmnt -lo source,target,fstype,label,options,used -t ext4SOURCE    TARGET                                      FSTYPE LABEL OPTIONS  USED
/dev/sda1 /                                           ext4         rw,rela 14,6G
/dev/sdb1 /media/aelm/d0740038-9c96-481e-86c5-49656b56fdd8
                                                      ext4         rw,nosu 71,7M




Cheers.

---

### Post by Bashing-om on 2018-03-23
allosaurus66; Cheerfully 

> 
2- Is it a good place (or the best place) the mount point as it is or is better to mount it somewhere else?


For your present use case mounting in media will serve.

To make "you" the owner of the file system on the TeraByte disk we will want to verify the mount point.

Post back the result of terminal commands:
```

ls -al /media/
ls -al /media/aelm/

```
where are are looking for the ID of that partition and then "chown" it.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by allosaurus66 on 2018-03-23
Here:
> 
aelm@aelm-MS-7A70:~$ ls -al /media/
total 12
drwxr-xr-x   3 root root 4096 mar 23 17:56 .
drwxr-xr-x  24 root root 4096 mar 16 18:13 ..
drwxr-x---+  3 root root 4096 mar 23 17:56 aelm

aelm@aelm-MS-7A70:~$ ls -al /media/aelm/
total 12
drwxr-x---+ 3 root root 4096 mar 23 17:56 .
drwxr-xr-x  3 root root 4096 mar 23 17:56 ..
drwxr-xr-x  3 root root 4096 mar 23 17:17 d0740038-9c96-481e-86c5-49656b56fdd8



---

### Post by Bashing-om on 2018-03-23
allosaurus66; there

```

sudo chown aelm:aelm /media/aelm/d0740038-9c96-481e-86c5-49656b56fdd8

```


[INDENT][INDENT]you can do it
[/INDENT][/INDENT]

---

### Post by allosaurus66 on 2018-03-23
@Bashing-om 
Thanks a lot. Everything works fine. I followed your command line and it took a few seconds to work right. After the chown everything was the same,  but then it worked.

I click on properties and I am the owner. Files can go in and out.
Great!  

Than you very much all of you guys. Great team you are. I hope this closes this matter.

Cheers!

---

### Post by Bashing-om on 2018-03-23
allosaurus66; Outstanding ..

as other questions arise -

[INDENT][INDENT]you know where we live
[/INDENT][/INDENT]

---

### Post by allosaurus66 on 2018-03-23
Sure! 
One last thing:

I just thought: shall I edit fstab and mstab?

---

### Post by Bashing-om on 2018-03-23
allosaurus66; Hey -

> 
I just thought: shall I edit fstab and mstab?


Not necessarily - depends on your use case . Me, I only mount my data partitions "on-demand" from terminal.

Now if you DO want the 1TB always available upon boot up, then yes make the mount in /etc/fstab .
If you do not want to see the drive in the GUI then change the mount point from /media/.


keep in mind
[INDENT][INDENT]if it ain't broke do not fix it
[/INDENT][/INDENT]

---

### Post by oldfred on 2018-03-23
If you create a mount point then that is the name/label it will be seen by.
But I also label all partitions, so that the auto mount in /media/fred is by label which I can understand and not the very long UUID which I do not then know which is which.

Example:

```
fred@Z170N:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4         bionic      25.4G c29fc361-ea05-420b-b919-850aeef65dd4 /mnt/bioni
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 /media/fre
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8 yakkety yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 /media/fre
```

---

### Post by allosaurus66 on 2018-03-24
Ok, thanks. I will mount on "demand", I guess.

Cheers.

---

### Post by allosaurus66 on 2018-03-24
@oldfred

Good tip. Thanks.

Cheers.

---


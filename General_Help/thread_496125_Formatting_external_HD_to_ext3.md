---
title: "Formatting external HD to ext3"
date: 2007-07-08
forum: General Help
---

### Post by Johnny K on 2007-07-08
I just bought an external hard drive, but it is NTFS. How do I format it to ext3, so that I can write to it?

TIA :)

---

### Post by southernman on 2007-07-08
I assume that ubuntu can see the drive and mounts it for you, so do...

> sudo fdisk -lsu

take the info from that and do...

> sudo fdisk <insert device name here>

where device name is probably /media/sd? or /dev/sd?
The above command will dump you into the fdisk tool where you simply type m for a listing of commands to use. I would do the following in order in fdisk:

d (will delete partitions)
enter the partition number to delete, most like it's only one and will do it for you.

n (create a new partition)
choose to make a primary or extended (p or e)
next choose the partition number (1)
then your going to be prompted to setup the start block, just enter for default.
then you'll be prompted for the ending block, just enter to use the entire drive.

w (will write the partition table and do a quick check for you.

q (will end fdisk and dump you to your normal command prompt.

Now you need to format the partition which is detailed at the link below...
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

hth's though someone probably already beat me to it! :p

*Could of saved myself a lot of typing as the link above tells you this, plus how to format it. Be sure to do the reserved blocks tweak too. Gives YOU more room, not the OS. ;)

---

### Post by Johnny K on 2007-07-08
Just to be sure, could this be the external hard drive?

Disk /dev/sdb: 120.0 GB, 120034123776 bytes

I just want to be sure. The external drive is 120gb. Is there any other way I can be sure it's the right one?

***Edit:** That was the one. Thanks for the help!*

---

### Post by Johnny K on 2007-07-08
A new problem:

The drive is ext3 now, but the permissions are as follows:
Root - Create and delete files
Group (root): Access files
Others - Access files

What should I change the permissions to, and how?

---

### Post by southernman on 2007-07-08
> **Johnny K said:**
> A new problem:

The drive is ext3 now, but the permissions are as follows:
Root - Create and delete files
Group (root): Access files
Others - Access files

What should I change the permissions to, and how?

No problem with the first part.... your welcome! ;)

To solve the ownership, just do...

```
sudo chown -R username:username /dev/sdb
```

---


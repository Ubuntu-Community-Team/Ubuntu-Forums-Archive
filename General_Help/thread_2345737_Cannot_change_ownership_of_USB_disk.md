---
title: "Cannot change ownership of USB disk"
date: 2016-12-07
forum: General Help
---

### Post by frankh on 2016-12-07
System: Ubuntu Server 16.4

USB disk 1: USB "thumb drive", 32GB. ExtFat. Mounted as /mnt/usb

- On this disk, I'm able to chown all files and folders to any user.

USB disk 2: USB, 1TB. NTFS. Mounted as /mnt/usb2

- On this disk, I'm unable to chown any files or folders. There is no error returned from the chown command, but the ownerships are not changed. They're stuck at root:root.

Any ideas? Is it an issue with NTFS?

---

### Post by frankh on 2016-12-07
System: Ubuntu Server 16.04

First, the USB drive was formatted as NTFS in Windows, then mounted in Ubuntu as /dev/sdc1 to /mnt/usb/

- Impossible to change ownership of files or folders created on the drive. Everything is owned by root:root. No error messages from chown; just nothing happening.


I gave up on that, umounted the /sdc1 disk, then created a new partition with fdisk:

$ sudo fdisk /dev/sdc

Then o, to create a new empty DOS partition table,
n to add a new partition (the whole disk),
w to write the table to disk and exit

$ sudo mkfs.vfat /dev/sdc1
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1       65535 244190645 244125111 931.3G 83 Linux


Looks ok, doesn't it?

Then I mounted it:

$ sudo mount /dev/sdc1 /mnt/usb

Created a folder on the disk:

$ sudo mkdir /mnt/usb/test

Now, naturally this is owned by root. However, I don't want it to be. I want the folder and all files and subfolders to be owned by the user and group 
debian-transmission:debian-transmission

So, I try:

$ sudo chown -R debian-transmission:debian-transmission /mnt/usb/test/

And the nice error message:

chown: changing ownership of '/mnt/torrents/transmission/': Operation not permitted


What gives?

---

### Post by coffeecat on 2016-12-07
Threads merged. Please don't open duplicate threads on the same subject - it dilutes community effort and causes confusion.

NTFS is a Microsoft filesystem which does not support the Unix set of permissions and ownership used in Linux operating systems. Permissions are set globally on a NTFS filesystem by the mount options. The chmod and chown commands simply won't work with NTFS.

I'm sure someone will amplify this and give you more details.

---

### Post by frankh on 2016-12-07
Hi admin. If you read the questions, you'll see that it's not the same question. However, I could have merged them, I agree.

But why are you talking about NTFS when my last question clearly states that I created a native Linux partition on the drive, and the problem is now that chown returns "operation not permitted".

I removed the disk again, reformated it to Fat32, but the problem is still present. I get "operation not permitted" when trying to chown files or folders on the drive. If I try to chmod (a+rwx), I get no error, but the permissions never change.

I even tried the following:

- Created a folder /home/usb
- Chowned the folder to the user/group debian-transmission:debian-transmission
- Mounted /dev/sdc1 in /home/usb

Even THEN, I get "operation not permitted" when I try to chown the files/folders!

This seems profoundly broken? Where can I find someone who can help with this?

However: With the disk formatted with Fat32, I AM able to mount the disk with a specified user:group, like this:

   sudo mount -o rw,uid=111,gid=118,user,exec,umask=003 /dev/sdc1 /mnt/torrents/

But: Is there no way to do this with an NTFS partition? How about a native Linux partition, created with fdisk in Ubuntu? The problem with Fat32 is the max filesize of 4.2GB, which is a bit archaic nowadays.

---

### Post by coffeecat on 2016-12-07
I was answering your first question - "Any ideas? Is it an issue with NTFS? "

I didn't answer anything else because I can't make sense of what you say here:

[quote=frankh]$ sudo mkfs.vfat /dev/sdc1
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1 65535 244190645 244125111 931.3G 83 Linux[/quote]

That information tells me that you created a vfat filesystem in sdc1 with mkfs and then immediately after that, fdisk says that sdc1 is formatted with a Linux filesystem, which appears to be a contradiction. Is there something missing? Perhaps you could clarify.

Anyway, as for NTFS so for FAT32. Another Microsoft filesystem that doesn't support Unix permissions and on which you cannot use the chmod or chown commands.

As to...

> Where can I find someone who can help with this? 

Be patient. I'm sure someone on this **volunteer** forum will be along shortly.

---

### Post by ajgreeny on 2016-12-07
Let's go back to the beginning and ask what you want when all this is sorted out.

Do you want all users to be able to read and write to the USB disk without any permissions problems?
If so then both **fat32** and **ntfs** file systems should be fine by default without the need for you to have to worry about **chmod** or **chown** commands.  However, if you wish to limit who can read and write to the USB drive as users you will be much better served by formatting their partitions as ext4 as you will then be able to give files and folders appropriate permissions.

Tell us more, please.

---

### Post by frankh on 2016-12-07
Sorry for the sour tone; I tend to get that way after a couple of hours with banging my head on the keyboard. I can usually suck it up, though.

Ok, to recap:

ajgreeny:

I want a folder, with files and subfolders, on the USB drive which ownership is user:group other than root, and which I need to be able to specify. Only once, though, so it can be also done on mount.

The strange thing is, I already have a small 32GB USB stick connected to the server, with 32GB. That drive is formatted with Fat32, and I was able to chown and chmod it without problems. Worked like a charm. That's kind of why I was expecting at least Fat32 on the new 1TB drive to work the same way. But obviously it's not.

So, in my specific case I want to set the ownership to a specific user AND set the permission so that everyone can read it (and share it with Samba).

coffeecat:

$ sudo mkfs.vfat /dev/sdc1
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1 65535 244190645 244125111 931.3G 83 Linux

This is the exact output. I was also surprised to see that vfat was suddenly identified as Linux. But from the fdisk output, I thought the disk was now a Linux native one. But I gues it's not? Anyway, when I tried chowning it afterwards, I got the "operation not permitted" error, which made me a bit fed up (which was why I wondered if ANYONE could help - no offence intended, just tiredness).

So, what I need is to format the disk with a filesystem that allows me to mount it, and have either the whole disk or a folder with subfolders owned by a specific (non-root) user. And, of course - I need to be able to share it with Samba, but that's another headache for a later day.

So, sorry for my ignorance, but it's been a while since my old "linux days", and fs considerations and trouble is something I've managed to mostly avoid. But if the ticket here is to format the USB-drive witht ext4, and that will let me have full control over the ownerships and permissions, as well as share it with Samba, that's what I want/need/crave. Is a how-to for that doable in a few lines here, or should I start crawling the net for more or less credible articles/sources?

---

### Post by frankh on 2016-12-07
Ok, to recap:

ajgreeny:

I want a folder, with files and subfolders, on the USB drive which ownership is user:group other than root, and which I need to be able to specify. Only once, though, so it can be done on mount.

The strange thing is, I already have a small 32GB USB stick connected to the server, with 32GB. That drive is formatted with Fat32, and I was able to chown and chmod it without problems. Worked like a charm. That's kind of why I was expecting at least Fat32 on the new 1TB drive to work the same way. But obviously it's not.

coffeecat:

$ sudo mkfs.vfat /dev/sdc1
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1 65535 244190645 244125111 931.3G 83 Linux

This is the exact output. I was also surprised to see that vfat was suddenly identified as Linux. But from the fdisk output, I thought the disk was now a Linux native one. But I gues it's not? Anyway, when I tried chowning it afterwards, I got the "operation not permitted" error, which made me a bit fed up (which was why I wondered if ANYONE could help - no offence intended, just tiredness).

So, what I need is to format the disk with a filesystem that allows me to mount it, and have either the whole disk or a folder with subfolders owned by a specific (non-root) user. And, of course - I need to be able to share it with Samba, but that's another headache for a later day.

---

### Post by kpatz on 2016-12-07
FAT/FAT32/VFAT and NTFS aren't Linux native file systems, and don't recognize Linux ownership and permissions.

If you want to mount a NTFS partition and have it be "owned" by you, you'll have to get your UID and GID using the id command.  Often in Ubuntu the first installed user has a UID and GID of 1000, so we'll use that in this example.

Then when you mount the partition, specify the UID and GID as such.  Also specify a umask that will make the permissions the way you want.  A umask of 002 will give you 775 permissions.

```
sudo mount -o uid=1000,gid=1000,umask=002 /dev/sdc1 /mnt/usb2
```

You gave your partition an ID of linux, but then you formatted it as vfat.  If you want to format the drive with an actual Linux native filesystem that recognizes ownership and permissions, use mkfs.ext4.

---

### Post by frankh on 2016-12-07
I tried mounting the NTFS partitionthe way you described. However, I don't remember the exact error message, but I think it was something about bad blocks and/or unknown file system. 

But is there any reason not to use ext4, as long as the disk doesn't have to be read anywhere else?

---

### Post by kpatz on 2016-12-07
You already reformatted the disk, so it's not NTFS anymore... if you're only going to use it with Ubuntu, format it as ext4 and call it a day.  Then ownership and permissions will work as you expect.

---

### Post by #&amp;thj^% on 2016-12-07
> **kpatz said:**
> You already reformatted the disk, so it's not NTFS anymore... if you're only going to use it with Ubuntu, format it as ext4 and call it a day.  Then ownership and permissions will work as you expect.

+1;)

---

### Post by ajgreeny on 2016-12-07
> **kpatz said:**
> You already reformatted the disk, so it's not NTFS anymore... if you're only going to use it with Ubuntu, format it as ext4 and call it a day.  Then ownership and permissions will work as you expect.
Are you sure about that?  
There seems to be something strange going on here, or perhaps the output of the commands shown by frankh in his comment to coffeecat are explained in a way that I do not understand!
```
coffeecat:

$ sudo mkfs.vfat /dev/sdc1
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1 65535 244190645 244125111 931.3G 83 Linux

This is the exact output.
```

---

### Post by kpatz on 2016-12-07
> **ajgreeny said:**
> Are you sure about that?  
There seems to be something strange going on here, or perhaps the output of the commands shown by frankh in his comment to coffeecat are explained in a way that I do not understand!
```
coffeecat:

$ [COLOR="#FF0000"]sudo mkfs.vfat /dev/sdc1[/COLOR]
$ sudo fdisk -l |grep sdc

Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 244190646 sectors
/dev/sdc1 65535 244190645 244125111 931.3G 83 [COLOR="#0000FF"]Linux[/COLOR]

This is the exact output.
```The code in red is where he reformatted the disk as VFAT.  The output in blue is where he thought it was telling him he had a native Linux filesystem, when that's just the partition type.

---

### Post by ajgreeny on 2016-12-08
The fdisk output I expect from a fat32 USB disk should be similar to what I show below from my system with a fat32 USB attached.
Why would fdisk report an **83 Linux** partition; it just does not make any sense to me.
```
Disk /dev/sdf: 500.5 MiB, 524811776 bytes, 1025023 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xba919da0

Device     Boot Start     End Sectors  Size Id Type
/dev/sdf1        2048 1023999 1021952  499M  b W95 FAT32
```

---


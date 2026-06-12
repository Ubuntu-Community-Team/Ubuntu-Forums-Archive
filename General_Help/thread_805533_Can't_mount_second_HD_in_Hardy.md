---
title: "Can't mount second HD in Hardy"
date: 2008-05-24
forum: General Help
---

### Post by chaskins on 2008-05-24
Hi,

I upgraded to Hardy last night and now I can not mount my second hard drive, which I had no problems mounting in 7.10.
When I do a:

```
sudo fdisk -l
```

it shows up in the list as /dev/sdb1:

output:
```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

```

But when I try to mount it using:

```
sudo mount -t ext3 /dev/sdb1 /storeage
```

I get the following error:

```
mount: special device /dev/sdb1 does not exist
```

Any one have any ideas as this is driving me crazy and I would rather not lose the data on this disk.

Thanks

Chris

---

### Post by geo909 on 2008-05-24
> **chaskins said:**
> Hi,

But when I try to mount it using:

```
sudo mount -t ext3 /dev/sdb1 /storeage
```

I get the following error:

```
mount: special device /dev/sdb1 does not exist
```

Any one have any ideas as this is driving me crazy and I would rather not lose the data on this disk.


I don't think you will lose data from your disk in anyway.

Did you try to enter the mount command to your fstab file?

There is a graphical tool called pysdm (Python Storage Device Manager).
I've always found it very handy.
You can install it from synaptic and then try to configure how your device is handled.. ..if it can "see" you device, of course.

---

### Post by cdtech on 2008-05-24
There should be a MAKDEDEV command in your /dev directory, so try:

sudo /dev/MAKEDEV sdb

Then try the: sudo mount -t ext3 /dev/sdb1 /storeage

---

### Post by Kevbert on 2008-05-24
> **geo909 said:**
> 
There is a graphical tool called pysdm (Python Storage Device Manager).
I've always found it very handy.
You can install it from synaptic and then try to configure how your device is handled.. ..if it can "see" you device, of course.

Thanks, it looks very useful as I being trying out different linux flavours and fstab always gets mucked up.

---

### Post by chaskins on 2008-05-25
Hi,

Thanks for the replies. I have tried the suggestion but still nothing.

I installed pysdm and there is sdb in the list of partitions but no sdb1 etc so unable to configure.

I also tried the MAKEDEV command and mount but got the following:

```
mount: special device /dev/sdb1 does not exist
```

Any more ideas?

Cheers

Chris

---

### Post by cdtech on 2008-05-26
> I also tried the MAKEDEV command and mount but got the following:

What did you get when you ran the above command? Also be sure to run that command within the "/dev" folder.

Sometimes the special dev is located within the /dev/.static/ folder, but I wouldn't know in your case without seeing the output of the MAKEDEV command.

You obviously have the dev and the partition to mount, just not the correct location of the device.

In some cases it's necessary to mount the device using /dev/.static/dev/sdb1, but I would have to see the outcome of the command.

Hope this helps........

---

### Post by chaskins on 2008-05-27
Hi,

An update. I reinstalled ubuntu 7.10 and the second hard drive was detected as an IDE drive hdc and I was able to mount it. So I upgraded that installation to 8.04 my hard drives are showing up as IDE (hda, hdc). However upon booting I get an error message about not being able to find my second hard drive.

My /etc/fstab now looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cd8115a9-2f82-4e67-8a71-1879e63a327a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=de0d9eb2-52ef-4c72-aec0-252ff427358a /media/hdc1     ext3    defaults        0       2
# /dev/hda2
UUID=d68420c2-9a63-41ef-a9cb-91874502c741 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

When I run

```
sudo mount -a
```

I get the following error message:

```
mount: special device /dev/disk/by-uuid/de0d9eb2-52ef-4c72-aec0-252ff427358a does not exist
```

This is leading me to think that there is a bug in 8.04. Is it worth reporting or is there something glaringly obvious that I am not doing?

Thanks

Chris

---

### Post by chaskins on 2008-05-29
I'm still unable to mount this, any help?

---

### Post by Ziggy72 on 2008-05-29
This has now got too confusing for me (or probably anybody to help). If you still want help please post the output for fdisk -l and also your fstab file if it has changed in any way at all since you last posted 2 days ago. In other words, we need to know the exact status of your fstab and your partition info NOW. Actually, fdsik -l is the most important info we need.

---

### Post by cdtech on 2008-05-29
Now that you've reinstalled, you'll have to start over, somewhat. Like ziggy said "we'll have to see the output of fdisk -l again".

Sorry.....

---

### Post by chaskins on 2008-05-30
Hi,

Sorry for the confusion. I reinstalled 7.10 to make sure it wasn't the hard drive that was dead, as it worked before I upgraded to 8.04.

My /etc/fstab is still the same, but I'll put it below to keep things clear:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cd8115a9-2f82-4e67-8a71-1879e63a327a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=de0d9eb2-52ef-4c72-aec0-252ff427358a /media/hdc1     ext3    defaults        0       2
# /dev/hda2
UUID=d68420c2-9a63-41ef-a9cb-91874502c741 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

And now when I run fdisk -l I get the following output for my second hd:


```

....
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
```

Note: in the fstab it labels the second hard drive as hdc1, but in this output it is sdb1.

So when I run 'mount -a' I get the following error:

```
mount: special device /dev/disk/by-uuid/de0d9eb2-52ef-4c72-aec0-252ff427358a does not exist
```

When I try manually I get a similar message.

In summery, second hard drive can be mounted in Ubuntu 7.10 but when I upgraded to Ubuntu 8.04 I don't seem to be able to even though it shows up via the 'fdisk -l' command.

Thanks again for the help.

Regards,

Chris

---

### Post by plucky on 2008-05-30
@chaskins

> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux


Your second drive in Hardy is now using the designation for sata drives,so hda becomes sda. You are trying to mount media/hdc1 with your old fstab file and that does not exist.

Can you post the whole output of ```
sudo fdisk -l
``` and ```
ls -l /dev/disk/by-uuid
``` that is lowercase L not a 1.


See this tutorial on Psychocats website for [Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux)


Good Luck

---

### Post by chaskins on 2008-05-30
Full Output from *'fdisk -l'* (both disk are ide)

```
chris@Manta:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfeabfeab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
chris@Manta:~$ 

```

Output from *ls -l /dev/disk/by-uuid*

```
chris@Manta:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-05-30 17:07 cd8115a9-2f82-4e67-8a71-1879e63a327a -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-30 17:07 d68420c2-9a63-41ef-a9cb-91874502c741 -> ../../sda2
chris@Manta:~$ 

```

In the mean time I will read the tutorial, thanks for that.

Chris

---

### Post by cdtech on 2008-05-30
chaskins, I would do away with the uuid and just put the /dev/sdb1 in its place. Just make another directory such as /media/sdb1 (or whatever) and use that as your mount point.

Like:
```
/dev/sdb1     /media/sdb1     ext3    defaults        0       2
```

That should get you mounted, then we can add the uuid if needed.

Just sudo mount -a afterwards.

---

### Post by chaskins on 2008-05-31
Thanks for that. I have updated my fstab file as you suggested and then ran *sudo mount -a*

I got the following message back:

```
mount: special device /dev/sdb1 does not exist
```

So although I can see it with fdisk -l I don't seem to be able to mount it :(

Chris

---

### Post by plucky on 2008-05-31
Try from a terminal window

```
gksudo nautilus
```

Enter password,

A file browser window will open.
In the tool bar,click on **Computer**
If you can see a drive that says 160Gb media,then that should be your second hard drive.
Double click on it to mount it.It should then appear on your desktop.

If this works then your system can see it and access it.You will only have root access until you change permissions on the drive as outlined in Psychocats tutorial.

Good luck

---

### Post by chaskins on 2008-05-31
I tried that and have attached a screen shot showing what I have. The 160GB drive has come up, I think, as 'SCSI Drive' and when I try to open it it says it can not mount :(

Chris

---

### Post by plucky on 2008-05-31
> The 160GB drive has come up, I think, as 'SCSI Drive' and when I try to open it it says it can not mount

I am at a loss.

Do you have anything important on that disk?

What does Gparted make of the disk? 

If you start the partition editor,there is option to checkout the file system.

System > Administration > Partition Editor > Select drive > Partition > Select partition > Check.

See what that does.  Good Luck

---

### Post by chaskins on 2008-06-01
Ahh, I thought I has solved this. Let me explain :)

I ran up the 7.10 Live CD and was able to mount the hard drive, with no problems. I then copied all data off of the HD and rebooted back into Hardy.

Using gpart I repartitioned the hard drive and then mount it.
Sure enough looking on the computer section of the File Browser it showed up as 'media 160Gb' :)

However when I reboot it seems to lose all info about the HD and I have to go through the same process with gparted to get it mounted again.

I get the following error put into /var/log/fsck/checkfs

```
Log of fsck -C3 -R -A -a 
Sun Jun  1 08:22:56 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sun Jun  1 08:22:56 2008
----------------

```

The /etc/fstab has been updated, by gparted and now looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cd8115a9-2f82-4e67-8a71-1879e63a327a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
/dev/sdb1	/media/sdb1	ext3	defaults	0	2
# /dev/hda2
UUID=d68420c2-9a63-41ef-a9cb-91874502c741 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Is there something else I have missed?

cheers

Chris

---


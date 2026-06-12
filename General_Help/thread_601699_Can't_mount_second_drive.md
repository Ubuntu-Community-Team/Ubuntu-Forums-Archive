---
title: "Can't mount second drive"
date: 2007-11-03
forum: General Help
---

### Post by sonicjosh on 2007-11-03
I can not mount my other hdd, here is what shows up when I try:
[IMG]http://i28.photobucket.com/albums/c232/sonicjosh789/Screenshot.png[/IMG]
It only happened after I upgraded to Gutsy, it also happens with Gnome (ubuntu, im using xfce)
I tried both options (well i can't safely remove my windows hdd while i'm using it) I need to be able to mount it, All of my music is on it and I would like to be able to listen to it on xu/ubuntu.

---

### Post by ofb on 2007-11-03
Let's have a look at the output for these two,

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by sonicjosh on 2007-11-03
> **ofb said:**
> Let's have a look at the output for these two,

```
cat /etc/fstab
sudo fdisk -l
```

```
sonicjosh@sonicjosh-desktop-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c42b9b8a-14f2-4a61-952b-2baea4744afc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=37392658-323a-4fdc-b4e2-1fd638473e4c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
sonicjosh@sonicjosh-desktop-ubuntu:~$ sudo fdisk -l
[sudo] password for sonicjosh:

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38323831

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24792   199141708+  44  Unknown

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062985

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris
sonicjosh@sonicjosh-desktop-ubuntu:~$ 

```

Also, it is a 200gb hdd (if you didn't find that out in the image) and it contains windows, ubuntu is on a 80gb disk.

---

### Post by ofb on 2007-11-03
Well, it's a little funny the fstab shows hda as Linux, but that's commented out - you're actually using UUID, so it shouldn't matter.

But it's much more curious that your partition output shows System Unknown for your Win drive. I'm tempted to add the Win drive to fstab, but that 'Unknown' isn't giving me warm fuzzies.

How about trying a mount command with the Win drive's UUID instead of /dev/hda1? To get your UUID list use this,

```
ls /dev/disk/by-uuid/ -alh
```

Then mount would look like the next line, where 'xxxx' would be the number you just retrieved, and '/media/disk' is a pre-existing empty target directory.

```
mount UUID=xxxxx /media/disk
```

We're not specifying '-t' and a file type, so mount should try to figure it out. Run 'man mount' to have a look at various options.

But I'm not liking this. Maybe first let's have a look at your output for 'dmesg'. Incidently, run 'dmesg' right after a boot, or the output will be full of post-boot messages about your NICs and whatnot. We want to look at your IDE detection.

---

### Post by sonicjosh on 2007-11-04
I don't know if this is something simple but there is no /media/disk, I got into /media but it wont let me create a folder; It is probley something simple.

---

### Post by ofb on 2007-11-04
Yeah, the target mount point has to exist already. Also, only root can make directories in the system area.

So you could do something like 
```
sudo mkdir /media/disk
```

Or just use /mnt as your temporary mount point. That's usually sitting there empty for that purpose.

You can also make the mount point anywhere at all, of course. Like /home/[YourUserName]/music

Since that last one is within your /home section, you won't have to be root to create that directory.

While we're explaining things, another way of writing /home/[YourUserName]/music here on the forums is ~/music. The tilda is understood to mean the home directory of the current user. In commands though you would have to use the full form.

---


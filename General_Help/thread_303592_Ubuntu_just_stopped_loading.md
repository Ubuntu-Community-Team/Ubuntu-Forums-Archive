---
title: "Ubuntu just stopped loading"
date: 2006-11-20
forum: General Help
---

### Post by olieviya on 2006-11-20
I have now, very sadly, been forced to load windows since after 6 tries of loading up ubuntu I cannot get in. I get frozen at the loading stage, where there is the ubuntu/kubuntu logo and a loading bar under. I have no idea what to do. I am on an alienware 5550m and some specs: 128MB ATI Mobility Radeon X1400, 5400 RPM - Up to 120GB SATA with NCQ, 15.4” Wide Screen WXGA 1280 x 800... Not sure what else to put, please help!

---

### Post by strabes on 2006-11-20
I believe you can hit Ctrl + C during the loading process to kill whatever is causing it to crash. Also, I believe ctrl+alt+f1 shows the messages while booting. I'm not entirely sure though.

---

### Post by ap9er on 2006-11-21
I had a similar problem recently. Turned out that it wasn't finding my harddrive.

Ended up having to use a livecd and mounting the root filesystem to check my fstab (for some reason the drives had been quoted in).

---

### Post by olieviya on 2006-11-21
> **ap9er said:**
> I had a similar problem recently. Turned out that it wasn't finding my harddrive.

Ended up having to use a livecd and mounting the root filesystem to check my fstab (for some reason the drives had been quoted in).

How did you fix it? :S Exactly... me=n00b

---

### Post by ba5e on 2006-11-22
> **olieviya said:**
> How did you fix it? :S Exactly... me=n00b
To fix this do the following:

1)Boot up an Ubuntu LiveCD
2)Open terminal
3)sudo mkdir /mnt/ubuntu
4)sudo mount /dev/hdXx /mnt/ubuntu (where Xx is the disk/partition Ubuntu resides)
5)sudo gedit /mnt/ubuntu/etc/fstab
6)check your settings for / are correct (this is the 'root' file system)
7)Save the file, Reboot
8)Watch Ubuntu load :)

---

### Post by olieviya on 2006-11-23
> **ba5e said:**
> To fix this do the following:

1)Boot up an Ubuntu LiveCD
2)Open terminal
3)sudo mkdir /mnt/ubuntu
4)sudo mount /dev/hdXx /not/ubuntu (where Xx is the disk/partition Ubuntu resides)
5)sudo gedit /mnt/ubuntu/etc/fstab
6)check your settings for / are correct (this is the 'root' file system)
7)Save the file, Reboot
8)Watch Ubuntu load :)

I've managed to get Ubuntu loading after trying and now (last 5-6 times) it seems to be ok, do I still have to do the above? :-k




I had a problem with the boot up again and gave your advice a go, seems to be all ok now, cheers!

Btw the 4th step is not=mnt? because that is what i used... the not didn't exist

---

### Post by ba5e on 2006-11-26
> **olieviya said:**
> I've managed to get Ubuntu loading after trying and now (last 5-6 times) it seems to be ok, do I still have to do the above? :-k




I had a problem with the boot up again and gave your advice a go, seems to be all ok now, cheers!

Btw the 4th step is not=mnt? because that is what i used... the not didn't exist

There is mount and umount which are commands for monuning un-mounting filesystems, as far as I know mnt does not exist!

---

### Post by ba5e on 2006-11-26
> **ba5e said:**
> There is mount and umount which are commands for monuning un-mounting filesystems, as far as I know mnt does not exist!

oops I'm stupid!

Of course it should be mnt:

4)sudo mount /dev/hdXx /mnt/ubuntu (where Xx is the disk/partition Ubuntu resides)
I have changed to original post, thanks for the heads up ;)

---

### Post by shin on 2006-11-26
Oh come on. Solution without even knowing what is the problem?

First of all, turn off splash, at least for one boot.
If I recall correctly, in GRUB press e and change the command line for your Ubuntu installation.

remove 'quiet' and 'splash' if it is there, and add 'nosplash' word. Now it should run without splash and bars and other crap. Instead it will inform you about the progress of starting, all services status etc.

Now you will know when it fails, hangs up or anything.

Write down any errors and post them here.

---

### Post by olieviya on 2006-11-26
> **ba5e said:**
> oops I'm stupid!

Of course it should be mnt:

4)sudo mount /dev/hdXx /mnt/ubuntu (where Xx is the disk/partition Ubuntu resides)
I have changed to original post, thanks for the heads up ;)

Sorry your solution has not helped, I'm stuck out again:(


> **shin said:**
> Oh come on. Solution without even knowing what is the problem?

First of all, turn off splash, at least for one boot.
If I recall correctly, in GRUB press e and change the command line for your Ubuntu installation.

remove 'quiet' and 'splash' if it is there, and add 'nosplash' word. Now it should run without splash and bars and other crap. Instead it will inform you about the progress of starting, all services status etc.

Now you will know when it fails, hangs up or anything.

Write down any errors and post them here.

Ok, hmm, I can't seem to get the splash to go away.... I tried removing the word splash and replacing it with nosplash but, nothing!!!


Seems like I F*cked it up pretty badly.

/dev/sda2 has been mounted 30 times without being checked, check forced

BUG: soft lockup detected on CPU#0!
Checking file systems
WARNING: Bad format on line 5 of /etc/fstab
*Mounting local filesystems...

---

### Post by dexter on 2006-11-26
Try posting you /etc/fstab, maybe that'll help us help you.

---

### Post by shin on 2006-11-26
WARNING: Bad format on line 5 of /etc/fstab
*Mounting local filesystems...

what happens then? if anything? 
Any other errors after that? As dexter said fstab may be helpful.

---

### Post by olieviya on 2006-11-26
> **shin said:**
> WARNING: Bad format on line 5 of /etc/fstab
*Mounting local filesystems...

what happens then? if anything? 
Any other errors after that? As dexter said fstab may be helpful.

I think I have made a mistake with the editing of it :(



> **dexter said:**
> Try posting you /etc/fstab, maybe that'll help us help you.


Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


/dev/sda2       /        ext3    defaults,errors=remount-ro 0       1
/dev/sda5
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by shin on 2006-11-26
looks strange. maybe thats the problem

try removing line '/dev/sda5' so changing it to
```

proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

If it wont work, try 

```

proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

sda5 seems to be your swap but you may reference to it via /dev/ or via UUID. Not sure of advantages of UUID solution implemented in ubuntu from 6.10 (I think and I may be wrong)

---

### Post by olieviya on 2006-11-27
> **shin said:**
> looks strange. maybe thats the problem

try removing line '/dev/sda5' so changing it to
```

proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

If it wont work, try 

```

proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

sda5 seems to be your swap but you may reference to it via /dev/ or via UUID. Not sure of advantages of UUID solution implemented in ubuntu from 6.10 (I think and I may be wrong)
I managed to get it loading now:
I did this without knowing of your reply so I think I'll just post the changes I made because it works with them and you can tell me if it's ok;
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


/dev/sda2       /        ext3    defaults,errors=remount-ro 0       1
/dev/sda5
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by shin on 2006-11-27
I cant see a difference from your previous /etc/fstab :mrgreen:

There is no warning right now? This '/dev/sda5' line seems to be not needed.

Anyway glad to hear that you managed to make it work ;)

---

### Post by olieviya on 2006-11-27
> **shin said:**
> I cant see a difference from your previous /etc/fstab :mrgreen:

There is no warning right now? This '/dev/sda5' line seems to be not needed.

Anyway glad to hear that you managed to make it work ;)
It did have some more stuff written in some thing like: UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 for the root directory and the sda5 was commented out... I really ruined it, it had a lot more stuff written in there, is there any way to get that back?

ALSO for some reason the splash came back... do I have to remove it with grub every time?

---

### Post by shin on 2006-11-27
Actually /dev/sda5 should be commented out.
This is just a "description" for next line where it refers to sda5 with UUID.

I dont know easy way for finding device UUID. Anyway if you're usng hal, try
```
hal-device | grep volume
```

There you will find a list of (i think only acutally mounted) partitions with some properties like label, mount point, filesystem and UUID. ange

Still - there is no need to use UUID in fstab, you can use /dev/something instead.

You're saying that something is still missing. What is it? Is there any other partition or drive that is not mounted right now?

Oh and you need to edit /boot/grub/menu.lst to actually remove swap. When you change command line while booting - it doesnt save.

Find there something like

```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

remove quiet and splash

Or you may just remove quiet and there will be basic splash and all the information. Not sure though. Give me a sec, I'll reboot ;)

Yup. Removing quiet works pretty good if you want eyecandy and informations on progress. You may also check logs after you boot.
Basic information based on current boot - /var/log/boot

---

### Post by olieviya on 2006-11-27
> **shin said:**
> Actually /dev/sda5 should be commented out.
This is just a "description" for next line where it refers to sda5 with UUID.

I dont know easy way for finding device UUID. Anyway if you're usng hal, try
```
hal-device | grep volume
```

I commented it out :)

Ok, You'll need to help me with this:

[INDENT][COLOR="DimGray"][SIZE="1"][FONT="Courier New"]block.is_volume = false  (bool)
9: udi = '/org/freedesktop/Hal/devices/volume_uuid_EA943E7F943E4DF7'
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime
', 'noexec', 'quiet' } (string list)
  volume.ignore = false  (bool)
  volume.policy.desired_mount_point = 'scsidisk'  (string)
  volume.policy.mount_filesystem = 'ntfs'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_EA943E7F943E4DF7'  (strin
g)
  volume.partition.msdos_part_table_type = 7  (0x7)  (int)
  volume.size = 60011610624  (0xdf8f88200)  (uint64)
  volume.num_blocks = 117210177  (0x6fc7c41)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/windows'  (string)
  volume.label = ''  (string)
  volume.uuid = 'EA943E7F943E4DF7'  (string)
  volume.fsversion = '3.1'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'ntfs'  (string)
olivia@olivia-laptop:~$ hal-device | grep volume | more
  block.is_volume = false  (bool)
9: udi = '/org/freedesktop/Hal/devices/volume_uuid_EA943E7F943E4DF7'
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime
', 'noexec', 'quiet' } (string list)
  volume.ignore = false  (bool)
  volume.policy.desired_mount_point = 'scsidisk'  (string)
  volume.policy.mount_filesystem = 'ntfs'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_EA943E7F943E4DF7'  (strin
g)
  volume.partition.msdos_part_table_type = 7  (0x7)  (int)
  volume.size = 60011610624  (0xdf8f88200)  (uint64)
  volume.num_blocks = 117210177  (0x6fc7c41)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/windows'  (string)
volume.label = ''  (string)
  volume.uuid = 'EA943E7F943E4DF7'  (string)
  volume.fsversion = '3.1'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'ntfs'  (string)
  block.is_volume = true  (bool)
10: udi = '/org/freedesktop/Hal/devices/volume_uuid_b0c38602_aff8_4536_8656_57978aa9c7c6'
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'data=' } (string list)
  volume.ignore = true  (bool)
  volume.policy.desired_mount_point = 'scsidisk'  (string)
  volume.policy.mount_filesystem = 'ext3'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_b0c38602_aff8_4536_8656_57978aa9c7c6'  (string)
  volume.partition.msdos_part_table_type = 131  (0x83)  (int)
  volume.size = 57552284160  (0xd66622a00)  (uint64)
  volume.num_blocks = 112406805  (0x6b33115)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 2  (0x2)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/'  (string)
  volume.label = ''  (string)
  volume.uuid = 'b0c38602-aff8-4536-8656-57978aa9c7c6'  (string)
  volume.fsversion = '1.0'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'ext3'  (string)
  block.is_volume = true  (bool)
11: udi = '/org/freedesktop/Hal/devices/volume_part3_size_1024'
  info.udi = '/org/freedesktop/Hal/devices/volume_part3_size_1024'  (string)
  volume.partition.msdos_part_table_type = 5  (0x5)  (int)
  volume.size = 1024  (0x400)  (uint64)
  volume.num_blocks = 2  (0x2)  (int)
  volume.block_size = 512  (0x200)  (int)
volume.partition.number = 3  (0x3)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = false  (bool)
  volume.mount_point = ''  (string)
  volume.label = ''  (string)
  volume.uuid = ''  (string)
  volume.fsversion = ''  (string)
  volume.fsusage = ''  (string)
  volume.fstype = ''  (string)
  block.is_volume = true  (bool)
12: udi = '/org/freedesktop/Hal/devices/volume_uuid_5f3bd979_b523_40a0_aa82_ad0a5f249a85'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_5f3bd979_b523_40a0_aa82_ad0a5f249a85'  (string)
  volume.partition.msdos_part_table_type = 130  (0x82)  (int)
  volume.size = 2467551744  (0x9313da00)  (uint64)
  volume.num_blocks = 4819437  (0x4989ed)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 5  (0x5)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = false  (bool)
  volume.mount_point = ''  (string)
  volume.label = ''  (string)
  volume.uuid = '5f3bd979-b523-40a0-aa82-ad0a5f249a85'  (string)
  volume.fsversion = '2'  (string)
  volume.fsusage = 'other'  (string)
  volume.fstype = 'swap'  (string)
  block.is_volume = true  (bool)
  block.is_volume = false  (bool)
14: udi = '/org/freedesktop/Hal/devices/volume_uuid_147F_7F20'
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask
=', 'dmask=', 'fmask=', 'uid=' } (string list)
 volume.ignore = false  (bool)
  volume.policy.desired_mount_point = 'My Book'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  volume.policy.mount_option.quiet = true  (bool)
  volume.policy.mount_option.iocharset=utf8 = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_147F_7F20'  (string)
  volume.partition.msdos_part_table_type = 12  (0xc)  (int)
  volume.size = 250056705024  (0x3a388a8400)  (uint64)
  volume.num_blocks = 488392002  (0x1d1c4542)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/My Book'  (string)
  volume.label = 'My Book'  (string)
  volume.uuid = '147F-7F20'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  block.is_volume = true  (bool)
  block.is_volume = false  (bool)
[/FONT][/SIZE][/COLOR][/INDENT]
> **shin said:**
> 
You're saying that something is still missing. What is it? Is there any other partition or drive that is not mounted right now?

No, the uuid of root, but you say that it's not needed?
> **shin said:**
> 
Oh and you need to edit /boot/grub/menu.lst to actually remove swap. When you change command line while booting - it doesnt save.

Why would I want to remove swap? :-?  Oh, do you mean splash?


I commented it out like this, hope this is ok now:
[COLOR="DimGray"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


/dev/sda2       /        ext3    defaults,errors=remount-ro 0       1
#/dev/sda5
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
[/COLOR]

---

### Post by shin on 2006-11-27
My mistake, I meant splash ;)

Anyway based on your hal-device output:

/dev/sda1 has UUID EA943E7F943E4DF7 - your windows installation /media/windows
/dev/sda5 has UUID 5f3bd979-b523-40a0-aa82-ad0a5f249a85 - your splash and you already got the same in /etc/fstab
/dev/sda2 has UUID b0c38602-aff8-4536-8656-57978aa9c7c6 - your root partition mounted on /

There is also one more volume but thats probably some USB drive titled My Book.

There is no need to correct anything in your /etc/fstab right now but if you really want to change it to the way it probably was. It should be something like this:

```

proc /proc proc defaults 0 0
# /dev/sda2
UUID=b0c38602-aff8-4536-8656-57978aa9c7c6 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=5f3bd979-b523-40a0-aa82-ad0a5f249a85 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
# /dev/sda1
UUID=EA943E7F943E4DF7 /media/windows ntfs nls=utf8,umask=0222 0 0
```

And that should also work

---

### Post by olieviya on 2006-11-27
> **shin said:**
> 
There is also one more volume but thats probably some USB drive titled My Book.


Oh, thank you so much, yeah, that's an external drive, it doesn't need to be in there does it?

---

### Post by shin on 2006-11-27
No. Udev handles those. There is no need to put anything about it in fstab 8)

---

### Post by olieviya on 2006-11-27
> **shin said:**
> No. Udev handles those. There is no need to put anything about it in fstab 8)

Ok, well thanks a lot!!!
Byw the splash, I did what you said and it was ok, in other words I removed the quite and splash words from the end and replaced them with nosplash. But it didn't "save" it just loaded up, with no splash, but next time it had one.
Do I edit it on grub or do I edit it with Ubuntu already booted?

---

### Post by shin on 2006-11-27
Edit it in ubuntu already booted. Grub settings are in /boot/grub/menu.lst
Just edit those and save

---

### Post by olieviya on 2006-11-27
> **shin said:**
> Edit it in ubuntu already booted. Grub settings are in /boot/grub/menu.lst
Just edit those and save

Would going from this:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
to this:
```
title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

be something ok and have a little more info on the whole?

---

### Post by shin on 2006-11-27
Yes, that will work fine. You will get splash without bars and with text information about services starting.

To get more info about all options, try google. I'm not that familiar with grub.

Here is some theory behind booting process
[http://www.rt.com/man/initrd.4.html](http://www.rt.com/man/initrd.4.html)

---

### Post by olieviya on 2006-11-28
> **shin said:**
> Yes, that will work fine. You will get splash without bars and with text information about services starting.

To get more info about all options, try google. I'm not that familiar with grub.

Here is some theory behind booting process
[http://www.rt.com/man/initrd.4.html](http://www.rt.com/man/initrd.4.html)

Thanks, I'll read that when I get the chance :)

---

### Post by olieviya on 2006-12-05
I still have a problem :(
It says bug: soft error CPU#0 or something like that when loading...


PLEASE HELP!

---

### Post by olieviya on 2006-12-06
> **shin said:**
> Yes, that will work fine. You will get splash without bars and with text information about services starting.


I'm locked out again... what shall i do, I have not changed anything regarding what we changed together...](*,)

---

### Post by olieviya on 2006-12-07
i have managed to make it work now, the fstab file had been modified and made to have only 2 lines or irrelevant crap, what could have caused that? :-k :-k :-k

---

### Post by olieviya on 2006-12-24
I seem to be experiencing the infamous:

```
BUG: soft lockup detected on CPU#0!
```

and there seems to be nothing I can do... I have googled it and read quite a few other forums posts.... anybody got any bright ideas?;)

---

### Post by olieviya on 2007-03-06
My pc told me to so I tried serialize_io=0 and it seems to help, what does that do exactly?

---


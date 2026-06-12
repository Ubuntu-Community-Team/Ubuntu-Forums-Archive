---
title: "[SOLVED] EXT3 not supported in Ubuntu"
date: 2007-11-25
forum: General Help
---

### Post by DarkDancer on 2007-11-25
And yes before I start I understand the mistake that I made.

I have these 2 drives that are not being automounted since I reinstalled Ubuntu. I was trying to get them to automount and having trouble really understanding the entries in fstab. So I noticed that if you look at a mounted drive, in the properties, on the Volume tab, under settings there is mounting info. anyway, if you look at the pic, I messed that section up and now I can't mount them at all. I have to mount them to get to that screen. Is there another way I can get those dirves to mount or change what I mistakenly put in those options?

---

### Post by hikaricore on 2007-11-25
It's really hard to see what the problem is with linewrapping enabled in gedit...

Perhaps you should just post the contents of your /etc/fstab here?

---

### Post by DarkDancer on 2007-11-25
Here it is:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=ef160f9b-89cd-4ee6-82a0-b1ef58d094de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=a962120f-b19b-4e66-b624-717852aa6eda /home           ext3    defaults        0       2
# /dev/hda1
UUID=E32D93EF1FBFE70D /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=D91DEA0B4BE1DE89 /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=a084b93e-ea9d-49e0-817d-25b7e2d7159d /media/hda8     ext3    defaults        0       2
# /dev/hda5
UUID=7f3208b0-2ada-4b0d-a9c4-65ffc883edc9 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by hikaricore on 2007-11-25
You may want to check that your UUIDs are accurate.

Please run:

> ls /dev/disk/by-uuid -alh

From a terminal to get the correct UUIDs for each device.  ^_^

---

### Post by DarkDancer on 2007-11-25
Well, from what I can tell, those 2 drives are not in /etc/fstab. I have no idea how to get them there.

darkdancer@darkdancers:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 200 2007-11-25 21:47 .
drwxr-xr-x 6 root root 120 2007-11-25 21:47 ..
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 2a57aceb-dfb9-9520-983a-e26dbbdc4b95 -> ../../hdb1
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 7f3208b0-2ada-4b0d-a9c4-65ffc883edc9 -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 a084b93e-ea9d-49e0-817d-25b7e2d7159d -> ../../hda8
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 a962120f-b19b-4e66-b624-717852aa6eda -> ../../hda6
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 c567bf10-ab7e-4680-ec92-fb06ed0d8029 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 D91DEA0B4BE1DE89 -> ../../hda7
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 E32D93EF1FBFE70D -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 ef160f9b-89cd-4ee6-82a0-b1ef58d094de -> ../..

---

### Post by hikaricore on 2007-11-25
> **DarkDancer said:**
> Here it is:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Magenta"]# /dev/hda2
UUID=ef160f9b-89cd-4ee6-82a0-b1ef58d094de /               ext3    defaults,errors=remount-ro 0       1[/COLOR]
[COLOR="SeaGreen"]# /dev/hda6
UUID=a962120f-b19b-4e66-b624-717852aa6eda /home           ext3    defaults        0       2[/COLOR]
[COLOR="Red"]# /dev/hda1
UUID=E32D93EF1FBFE70D /media/hda1     ntfs    defaults,umask=007,gid=46 0       1[/COLOR]
[COLOR="DarkOrange"]# /dev/hda7
UUID=D91DEA0B4BE1DE89 /media/hda7     ntfs    defaults,umask=007,gid=46 0       1[/COLOR]
[COLOR="Blue"]# /dev/hda8
UUID=a084b93e-ea9d-49e0-817d-25b7e2d7159d /media/hda8     ext3    defaults        0       2[/COLOR]
[COLOR="DarkOrchid"]# /dev/hda5
UUID=7f3208b0-2ada-4b0d-a9c4-65ffc883edc9 none            swap    sw              0       0[/COLOR]
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

> **DarkDancer said:**
> Well, from what I can tell, those 2 drives are not in /etc/fstab. I have no idea how to get them there.

darkdancer@darkdancers:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 200 2007-11-25 21:47 .
drwxr-xr-x 6 root root 120 2007-11-25 21:47 ..
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 _2a57aceb-dfb9-9520-983a-e26dbbdc4b95_ -> ../../_hdb1_
**[COLOR="DarkOrchid"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 7f3208b0-2ada-4b0d-a9c4-65ffc883edc9 -> ../../hda5[/COLOR]**
**[COLOR="Blue"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 a084b93e-ea9d-49e0-817d-25b7e2d7159d -> ../../hda8[/COLOR]**
**[COLOR="SeaGreen"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 a962120f-b19b-4e66-b624-717852aa6eda -> ../../hda6[/COLOR]**
lrwxrwxrwx 1 root root  10 2007-11-25 21:47 _c567bf10-ab7e-4680-ec92-fb06ed0d8029_ -> ../../_sda1_
**[COLOR="DarkOrange"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 D91DEA0B4BE1DE89 -> ../../hda7[/COLOR]**
**[COLOR="Red"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 E32D93EF1FBFE70D -> ../../hda1[/COLOR]**
**[COLOR="Magenta"]lrwxrwxrwx 1 root root  10 2007-11-25 21:47 ef160f9b-89cd-4ee6-82a0-b1ef58d094de -> ../..[/COLOR]**

Easy enough if we compare the ones listed in your /etc/fstab to all the existing devices.

As you can see I color coded the existing ones, now you just need to add the missing two that I've underlined.
Simple as that.  ^_^

---

### Post by DarkDancer on 2007-11-25
The problem is I don't understand the command structure.

---

### Post by hikaricore on 2007-11-25
> **DarkDancer said:**
> The problem is I don't understand the command structure.

Oh I'm sorry, I misunderstood.

Here's something that may help.  ^_^

How to fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
And the community wiki page:  [http://help.ubuntu.com/community/Fstab](http://help.ubuntu.com/community/Fstab) (which is much less informative)

---

### Post by DarkDancer on 2007-11-25
hikaricore,

Thanks, the guide helped immensely! ;)

---


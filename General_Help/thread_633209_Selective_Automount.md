---
title: "Selective Automount?"
date: 2007-12-06
forum: General Help
---

### Post by Joe Momma on 2007-12-06
Is there a way to specify things that I don't want to mount automatically?

For instance I would like to be able to charge my ipod with the USB cable without it mounting and interrupting the music.  The same with my phone, without the SD card folders popping up and stuff.  However when I plug in my thumb drive, I don't want to have to mount it manually.

I know I can disable automounting of removable drives entirely, but  I was wondering if there was a way I could set a preference for individual items and have it remember them.

Thanks

---

### Post by viking777 on 2007-12-06
I presume you are using Gnome?

Switch to KDE and you will get a choice of what to do with any particular device every time you plug it in as well as a choice of remembering an action for any specific device type. From what I have gleaned from Gnome users that doesn't happen by default in Gnome but I don't use it so I don't know for sure.

---

### Post by Joe Momma on 2007-12-06
yes I do use gnome, and I have it all set up the way I like it.  I'd really prefer sticking with it.

If it's not possible, oh well, but I figured I'd check.

---

### Post by dreikin on 2007-12-06
EDIT: whoops, wrong thread..

---

### Post by jediborger on 2007-12-07
You can add entries to your fstab file that prevent automounting of certain drives/partition. And you can stick with Gnome :) This can be simpler by just using the /dev/xxx but often those names are used for several drives so this method uses a few more steps but will ensure only the drives you want 'ignored" don't get mounted.

First we'll find the UUID for the drive that you don't want mounted.
1. Plug in the drive and let it mount as usual and make note of what folder shows up eg. /media/disk
2. Fire up a terminal, Applications-Accessories-Terminal
3. Type "mount" and look to see what device (/dev/xxx) is mounted on /media/x from step 1 and note what fstype it is (vfat, ext3, etc)
4. Type "sudo vol_id /dev/xxx" from step 3
    Here's an example output:
```
matthew@laptop:~$ sudo vol_id /dev/sdc1
[sudo] password for matthew:
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=[COLOR="Blue"]44E9-2CDA[/COLOR]
ID_FS_UUID_ENC=44E9-2CDA
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```
     Make note of the blue text. You can select it from the terminal and Edit-Copy.

Next we'll add an entry to your fstab.
1. From the terminal type "sudo gedit /etc/fstab"
2. Add a line at the bottom, an example here will be easier to show.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8e6f17f2-75d6-411c-ac13-57aacff4c860 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=79B3992940B9EE2B /media/sda1     ntfs    defaults,noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3EC6-2E70  /media/sda2     vfat    defaults,noauto,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=5CC05DE4C05DC4C4 /media/sda3     ntfs    defaults,noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=5d469ff4-bf26-4061-86dc-337cfb1f502c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

#Look at this entry
UUID=[COLOR="Blue"]44E9-2CDA[/COLOR]	[COLOR="Red"]/media/cruze[/COLOR]r	[COLOR="Sienna"]vfat[/COLOR]	rw,user,noauto	0	0
```
     The blue should be changed for your drive UUID and the brown for the fstype.
     The red is the mount point and i recommend making your own so it doesn't conflict with other devices. If your mount directory doesn't exist, you'll need to create it first before you can mount the drive.
3. Save the file and close gedit.

Now unmount the drive, disconnect and reconnect. If all went well it shouldn't automount.
When you want to mount it just issue the command "mount UUID=*drive_id*" no sudo required.
Just repeat this process for each drive or partition on a device that you don't want automounted.

Remembering the UUID can be a pain though, if you want you can create a simple bash script to mount it for you such as:
```
#!/bin/bash

mount UUID=*drive_id*
```
You can also create special bash command by adding an alias. For example you can add the following to the end of your ~/.bashrc file:
```
alias mount-cruzer='mount UUID=*drive_id*
```
Then you can just enter "mount-cruzer" in a terminal or run dialog.

---

### Post by Joe Momma on 2007-12-10
I did that, but it still seems to mount the ipod, and the ipod stops playing and shows that ghostbuster sign.

---

### Post by mauritzius on 2008-04-01
unfortunately, this doesn't work for me either on Gutsy.
I tried using the gnome-mount utility, but there I can enter only mount-options; if I enter an invalid mount-option, it won't get mounted, but instead an error-message is displayed (which is annoying!)
Any other ideas?

Greetings

---

### Post by jediborger on 2008-04-01
What device are you using exactly? i don't have an Ipod but I've done this method with usb devices. Unless your device is the other type, I forget what the term is but nomad reads it. I'll run through what I wrote earlier and see if things have changed.

---

### Post by mauritzius on 2008-04-04
I'm using a SanDisk Cruzer, pretty much the same you used in your example.

---

### Post by mauritzius on 2008-04-04
Got it: You have to tell HAL to ignore the volume. I followed this guide:

[http://www.mandrivauser.de/doku/doku.php?id=hardware:internegeraete:fat_partition](http://www.mandrivauser.de/doku/doku.php?id=hardware:internegeraete:fat_partition)

It explains in detail (method 2) what you should do to get it mounted, so i set volume.ignore to true and my drive is now perfectly ignored!

greetings

EDIT: Sorry, didn't notice the page was in German! So, here the instructions:

Create a new file under /usr/share/hal/fdi/policy/20thirdparty and call it for instance ignore_cruzer.fdi

Contens of the file are:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- --> 
<deviceinfo version="0.2">
<device>

<match key="info.category" string="volume">
	<match key="@block.storage_device:storage.model" string="WDC WD1200BB-00DWA0">
		<match key="volume.uuid" string="40AF-74DA">
			<merge key="volume.ignore" type="bool">true</merge>
		</match>
	</match>
</match>

</device>
</deviceinfo>

```
Edit storage.model and volume.uuid to your needs (for instance using lshal) and all should be working fine!

---

### Post by antonr on 2008-04-05
An excerpt from the HAL 0.5.10 specification:
[http://people.freedesktop.org/~david/hal-spec/hal-spec.html#fdi-search-paths](http://people.freedesktop.org/~david/hal-spec/hal-spec.html#fdi-search-paths)
> **Search Paths**
Device Information files are read from two directories 
[LIST]
[*]/usr/share/hal/fdi - for files provided by packages
[*]/etc/hal/fdi - for files provided by the system administrator / user
[/LIST]
 in exactly that order. This means that the files provided by the system administrator will be processed last such that they can overwrite / change properties caused by the device information files provided by packages. 

Therefore, I think the correct place (for a sysadmin) to create a new .fdi file should be:

[INDENT]/etc/hal/fdi/policy/20thirdparty/[/INDENT]

---

### Post by mauritzius on 2008-04-06
yeah, I think you're right, I just copied the path from the webpage I referenced.

There is, however, one major pitfall in using this volume.ignore property: a user can't mount the drive using gnome-mount, the drive is even ignored in the filebrowser (of course, this is what volume.ignore is supposed to do).

Does anyone know about another solution that prevents the system from automounting, but allows the user to manually mount it?

thanks

---


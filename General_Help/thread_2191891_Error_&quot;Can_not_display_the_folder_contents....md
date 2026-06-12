---
title: "Error &quot;Can not display the folder contents...&quot; at Ubuntu 12.04.3"
date: 2013-12-04
forum: General Help
---

### Post by asgardsold on 2013-12-04
[COLOR=#000000][FONT=Verdana]Higuys,[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]I'&#7743; using a Ubuntu 12.04.3 x64 with the last updates and take a flash drive with a friend of mine that uses MAC OSX Laptop who tells me he was a big problem in a 4GB Sandisk flash memory, because he can't access and format it.[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]The description of issue are: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
When I insert  the flash memory at a USB port,automatically Ubuntu recognize it. But i click to open, takes looong time, didn't open and popups a error window: 

[B]Can not display the folder contents.You do not have the permisssion to see the contents of"C802-6D2D".
[/B]
When i tried format, it takes a loongtime too, and occurs that error: **Method "FilesystemUnmount"with signature "as" on interface"org.freedesktop.UDisks.Device" doesn't exist**

Bothof them, just after click “Ok” button error, the flash drive“disappear” and only returns when i remove and stick again.
Itried the following commands as root:[/FONT][/COLOR]


[B][COLOR=#000000][FONT=Verdana]chmod777 /media/C802-6D2D[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]chmod700 /media/C802-6D2D[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]chmod775 /media/C802-6D2D[/FONT][/COLOR]
[/B]

[COLOR=#000000][FONT=Verdana]And that occurs a similar error, flash memory disappear, with a one difference only: There was no error window.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
Thanks,[/FONT][/COLOR]

---

### Post by varunendra on 2013-12-06
Welcome to the forums asgardsold!

Guessing by the description and error messages, the flash drive is most probably corrupt. You may try a couple of things and if they don't work, it is most certainly gone.

1) Install Gparted (sudo apt-get install gparted) and try to delete existing partitions, if it can find any, and try creating a new partition table on it. If successful, try creating a new FAT32 partition on it and if that succeeds too, it will be usable again, although all its data will be lost.

2) Try using "dd" command to zero-fill the drive. If successful, you should be able to create new partition(s) on it again. For example, if it is detected by the OS as /dev/sdb, then -
```
sudo dd if=/dev/zero of=/dev/sdb bs=512
```
**[COLOR="#FF0000"]Be Very Careful !![/COLOR]** If used on wrong device (e.g., if /dev/sdb happens to be some other drive, not the flash drive in question), **[COLOR="#FF0000"]its data will be permanently lost and irrecoverable.[/COLOR]** So make sure you use the correct drive for "of=" option. If unsure, simply post back the output of -
```
sudo fdisk -l
``` after plugging in the drive.

None of the above will work if the flash drive is physically corrupt. Feel free to ask if you have more questions regarding this.

---


---
title: "gParted fails to 'initialise' micro sd card"
date: 2023-08-21
forum: General Help
---

### Post by johnaaronrose on 2023-08-21
GParted unable to read contents of FAT32 file system on micro sd card. I  have tried it with brand new 128 GB card as well as previously used  16GB card. I have installed mstools package; dosfstools package was already  installed. Computer is a month old one with Ubuntu 22.04 Desktop installed. 

[https://app.box.com/s/xdtd46f3qruwus9m0cqkgdfqs87p5j1g](https://app.box.com/s/xdtd46f3qruwus9m0cqkgdfqs87p5j1g)

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=292629&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-08-21
Does it show up in the results of
```

lsblk -e7 -o name,label,size,fstype,model

```

---

### Post by yancek on 2023-08-21
The image you posted shows Status not mounted.  Is that the problem, that you are unable to mount?  When you try to mount from a terminal, what happens?  Same result?

---

### Post by johnaaronrose on 2023-08-21
@ [ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1044547_2.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1044547") 				 				 					 						 	[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")
Yes, using the lsblk command you specified, though it shows up as vfat even though I 'initialised' it as Fat32.

---

### Post by johnaaronrose on 2023-08-21
@yancek Ubuntu mounts it when I remove it and re-insert it on my usb hub. Nautilus is able to read it and correctly shows it as empty.

---

### Post by #&amp;thj^% on 2023-08-21
> **johnaaronrose said:**
> @ [ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1044547_2.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1044547") 				 				 					 						 	[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")
Yes, using the lsblk command you specified, though it shows up as vfat even though I 'initialised' it as Fat32.

Nothing to write home about but, Output of commands like df and lsblk indeed shows vfat as the file system type. But sudo file -s /dev/<partition> shows FAT (32 bit) if a file system is FAT32.

You can confirm vfat is a module and not a file system type by running modinfo vfat.
Waving as I drive by.)):P

---

### Post by johnaaronrose on 2023-08-22
@1fallen 'sudo -s /dev/sda1' does show file system as Fat32. But back to my question "GParted says "Unable to read contents of this file system". Why is that occurring?

---

### Post by MAFoElffen on 2023-08-22
> **johnaaronrose said:**
> But back to my question "GParted says "Unable to read contents of this file system". Why is that occurring?
Why are you fixated on having GParted read it?

RE: [https://ubuntuforums.org/showthread.php?t=2411556](https://ubuntuforums.org/showthread.php?t=2411556)

TheFu, 1fallen, I and many ohter here answered many questions on how to look up information of attached storage devices. We also use command line tools to do that. There is many thread here of people asking why information cannot be read from GUI disk tools, such as Gnome Disks or GParted.... 

For instance, if you use GPatrted from an Installer LiveUSB, it has more options installed as default then when you install it in a distro, because in a distro, all the individual file systems and drivers need to be installed to the OS. 

vfat and FAT32 may seem to be fairly basic. The utilities to work with FAT filesystems are from the dosfstools package, which is not normally a default installed package. I manaully installed it on mine:
```

mafoelffen@Mikes-B460M:~$ apt list *fs*tools --installed
Listing... Done
dosfstools/jammy,now 4.2-1build3 amd64 [installed,automatic]
f2fs-tools/jammy,now 1.14.0-2build1 amd64 [installed,automatic]
guestfs-tools/jammy,now 1.46.1-4ubuntu2 amd64 [installed,automatic]
initramfs-tools/now 0.140ubuntu13.2 all [installed,upgradable to: 0.140ubuntu13.4]
libguestfs-tools/jammy,now 1:1.46.2-10ubuntu3 amd64 [installed]
squashfs-tools/jammy,now 1:4.5-3build1 amd64 [installed,automatic]

```
If you start GParted, and for a volume, right click and select format, then type... All the options that are grayed out, have missing filesystem 'pieces' that are not installed yet. Once they are installed, then those options are then enabled & selectable.

Does that answer your question on GParted?

---

### Post by johnaaronrose on 2023-08-22
@MAFoElffen I am NOT fixated on having gParted read the SD Card. Given that Nautilus can read the SD Card, it's obviously Ok and usable. 
The question I asked is: GParted says "Unable to read contents of FAT32 file system on micro sd card". I'm just intrigued about why gParted displays this error message. To me it seems to be a minor bug.

---

### Post by MAFoElffen on 2023-08-22
Because you created your own error on your disk... Even though it is there and formatted as FAT32 for a size of 119.05 GB:
> 
The FAT32 file system uses smaller clusters than the FAT file system, has duplicate boot records, and features a root directory that can be of any size and can be located anywhere on the disk or partition. The maximum possible size for a file on a FAT32 volume is **[COLOR=#ff0000]4 GB[/COLOR]**.

Then 
> 
Microsoft chose **[COLOR=#ff0000]32GB[/COLOR]** as the maximum partition size for a FAT32 file system. The main reason for this was to promote its new file system (NTFS), considered more efficient when working with large partitions. Despite that, the **[COLOR=#ff0000]32GB[/COLOR]** limit on FAT32 has influenced the file system differently.

So you created a partition formatted 87GB larger than the maximum capacity of the chosen filesystem... That is the biggest hurdle there. And why some things are having issues with it. Just because something is possible doesn't make it a good idea.

---

### Post by johnaaronrose on 2023-08-22
@MAFoElffen I am NOT fixated on having gParted read the SD Card. Given that Nautilus can read the SD Card, it's obviously Ok and usable. 
The question I asked is: GParted says "Unable to read contents of FAT32 file system on micro sd card". I'm just intrigued about why gParted displays this error message for both 16GB & 128GB. To me it seems to be a minor bug.
The reason that I 'set' the SD Card's partition to be Fat32 is that is what the instructions for the device (that I put it into) said to use a computer to format a SD Card if greater than 32GB as Fat32; for a 32GB SD Card the device would format it itself.

---

### Post by johnaaronrose on 2023-08-22
@MAFoElffen I am NOT fixated on having gParted read the SD Card. Given that Nautilus can read the SD Card, it's obviously Ok and usable.
The question I asked is: GParted says "Unable to read contents of FAT32 file system on micro sd card". I'm just intrigued about why gParted displays this error message for both 16GB & 128GB. To me it seems to be a minor bug.
The reason that I 'set' the SD Card's partition to be Fat32 is that is what the instructions for the device (that I put it into) said to use a computer to format a SD Card if greater than 32GB as Fat32; for a 32GB SD Card the device would format it itself.

---


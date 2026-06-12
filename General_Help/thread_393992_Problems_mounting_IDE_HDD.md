---
title: "Problems mounting IDE HDD"
date: 2007-03-26
forum: General Help
---

### Post by Viper_Maniac on 2007-03-26
[SIZE="1"]I wasn't positive where to put this so I hope I picked right.[/SIZE]

Not long ago I was having _[problems]("http://www.ubuntuforums.org/showthread.php?t=389714")_ installing Ubuntu on my system due to the fact I have a SATA(Ubuntu and Windows) and a IDE(Storage) HDD installed. Ubuntu, as well as Windows, kept going to the IDE drive as primary drive. So for both Windows and Ubuntu I disconnected the IDE drive to force both to use the SATA as primary. Windows I did over a week ago. Ubuntu I did a few days ago. Ubuntu kept installing grub to my IDE when I wanted it on the SATA. After getting the idea of doing what I did with Windows(see 3 sentences back) I decided to do that with Ubuntu as it should work just as well as it did with XP. So I did fixmbr on the IDE and then disconnected it. Installed Ubuntu and checked to make sure everything was fine. Then I reconnected the IDE drive. Windows recognizes it just fine but Ubuntu won't mount it. 

All I get after the "sudo mount -a" command is this:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Anything else to try?
-----------------------------------------------
Another thing I wanted to ask, I want to rename the name it gave my windows partition(sda1) to something more like Windows. How would I do that?

TIA for any help.

---

### Post by amdalex on 2007-03-26
Check you code you may have made a mistake. 
Try this if its NTFS- sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
If its FAT- sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
Only if hd is located at hda1, change accordingly.:mrgreen:

---

### Post by Viper_Maniac on 2007-03-27
It still gives me the same error.

```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Viper_Maniac on 2007-03-27
Nevermind what I said. It seems that my partition on the IDE drive was on hda5 instead of hda1 for some reason. I'm going to find out why that is because theres only one partition and it should be labeled hda1.

---


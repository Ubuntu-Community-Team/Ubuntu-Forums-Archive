---
title: "[SOLVED] Extra Partition is missing"
date: 2008-05-10
forum: General Help
---

### Post by Apex-jb on 2008-05-10
Solved.

I installed Hardy on one of two partitions on my laptop. The other partition is simply extra space and was FAT32. However, yesterday it simply disappeared. It no longer appears under "Places" and I can not figure out how to get it back. Anyone know what is going on here?

---

### Post by ghost_ryder35 on 2008-05-10
post the output of
```

gedit /etc/fstab

```

---

### Post by Apex-jb on 2008-05-10
> **ghost_ryder35 said:**
> post the output of
```

gedit /etc/fstab

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5db314ba-5fe2-40cc-b5a5-1d3b6b5da05d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=4C87-8D57  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a40dd95d-2f42-4b84-afc9-cc25661fe0b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---

### Post by vanadium on 2008-05-10
It appears as if it is not being mounted anymore, although it is in your /etc/fstab. To see the cause of the problem, execute the command

sudo mount -a

and post the output here. My guess is that a problem with the file system is preventing the partition from being mounted. Probably you will need to check the volume.

---

### Post by Apex-jb on 2008-05-10
Im not geting anything with sudo mount -a.

---

### Post by vanadium on 2008-05-10
Then your vfat partition is mounted. You will see its content navigating to /windows. If you want an icon on your desktop (and in the "Places" menu) for that partition, then mount it under /media/windows instead of /windows.

---

### Post by Apex-jb on 2008-05-10
.

---

### Post by Apex-jb on 2008-05-10
OK thanks. But how do I unmount it from /windows? I found it and it displays the correct amount of freespace but I dont know how to unmount and remount in a different location manually.

EDIT:I got it unmounted but still dont know how to mount it to media.

---

### Post by Apex-jb on 2008-05-11
bump

---

### Post by forestpixie on 2008-05-11
Make a directory for it to mount in -

```
sudo mkdir /media/windows
```

then backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.1105
sudo nano /etc/fstab[code]

Change this line 

> UUID=4C87-8D57  /windows        vfat    utf8,umask=007,gid=46 0       1

to 
> UUID=4C87-8D57  /media/windows        vfat    utf8,umask=007,gid=46 0       1

save the file with Ctrl+O, enter then Ctrl+X to exit

Not sure if [code]sudo mount -a
``` will do it, if not reboot and it should mount in /media/windows instead.

---

### Post by Apex-jb on 2008-05-11
Thanks, that did it.

---

### Post by forestpixie on 2008-05-11
Glad I could help - apparently the thread solved tool is back - so if you could :)

---

### Post by doncristobal on 2008-05-15
i have the same (a similar?) problem: i've just installed xubuntu hardy, and my extra partitions don't show up on the panel item 'places', nor on the desktop, although they are mounted and perfectly accessible+writable in /media. 
---
fstab: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=811efb7b-3cc9-4972-ab83-0a401bc1fa2f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=80009315-5e74-437f-8b07-2e5f3ecd61a5 /media/alt      ext3    relatime        0       2
# /dev/sda5
UUID=6AE3-F6DF  /media/data     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=5284826F8482557F /media/win      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=9f28e976-e780-4f07-b74a-5a0f373c062d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
---
sudo mount -a: no output at all
---
right-click - properties on 'places' does not give any option that sounds like solving my problem. 

can anyone give me a hint?

---


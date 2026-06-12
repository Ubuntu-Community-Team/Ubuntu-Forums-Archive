---
title: "Deciding mount name"
date: 2014-02-07
forum: General Help
---

### Post by James Wilde on 2014-02-07
There are lots of threads about mounting network disks, but none seems to address this problem.

I have finally managed to mount a disk sitting on my wife's Windows 7 machine on my Ubuntu 13.10.  I use the following command in a command file:

sudo mount -t cifs -o sec=ntlmssp,username=<wife's userid>,password=<wife's pw>,domain=workgroup,iocharset=utf8,file_mode=0777,dir_mode=0777 //192.168.1.102/Seagate /media/james

The reason I selected to mount it at /media/james was because the external disk I have attached to my ubuntu box also landed there.

What I now see in Nautilus is james in the left-hand window and Seagate in the right one, and I have to double click Seagate to see what's on it.  What I'd like to see in the left-hand window is Seagate (so I know what disk it is) and in the right, I'd like to see a list of the files and directories on the Seagate disk.

I've tried a few different varieties of the command above, but not managed to get what I want.

And before anyone asks why I mount the disk this way instead of via fstab, it's because my wife's computer isn't always switched on, and I dread to think what would happen to my startup time if ubuntu couldn't find the disk referred to in fstab.

Thanks for any help

---

### Post by ajgreeny on 2014-02-07
If you label the partitions with a partition manager such as gparted they will normally mount to your chosen mountpoint using a folder with same name as your label.

---

### Post by TheFu on 2014-02-07
/media is meant for portable mount points, so I try to avoid any conflicts by putting anything I manually mount that is NOT part of the OS under /D/.
I would think that this would get you what you want:
```

#!/bin/bash
mkdir -p /D/Seagate
sudo mount -t cifs -o sec=ntlmssp,username=<wife's userid>,password=<wife's pw>,domain=workgroup,iocharset=utf8,file_mode=0777 ,dir_mode=0777 //192.168.1.102/Seagate /D/Seagate
```

Then you'd use Nautilus to bookmark /D/Seagate. Does that make sense?

Another option to using this script would be to use **autofs**. As long as you or any process doesn't try to access the storage, no attempt to mount will happen. Not that there is anything wrong with having a script like you do.

---

### Post by bab1 on 2014-02-07
> **James Wilde said:**
> There are lots of threads about mounting network disks, but none seems to address this problem.

I have finally managed to mount a disk sitting on my wife's Windows 7 machine on my Ubuntu 13.10.  I use the following command in a command file:

sudo mount -t cifs -o sec=ntlmssp,username=<wife's userid>,password=<wife's pw>,domain=workgroup,iocharset=utf8,file_mode=0777,dir_mode=0777 //192.168.1.102/Seagate /media/james

The reason I selected to mount it at /media/james was because the external disk I have attached to my ubuntu box also landed there.

What I now see in Nautilus is james in the left-hand window and Seagate in the right one, and I have to double click Seagate to see what's on it.  What I'd like to see in the left-hand window is Seagate (so I know what disk it is) and in the right, I'd like to see a list of the files and directories on the Seagate disk.

I've tried a few different varieties of the command above, but not managed to get what I want.

And before anyone asks why I mount the disk this way instead of via fstab, it's because my wife's computer isn't always switched on, and I dread to think what would happen to my startup time if ubuntu couldn't find the disk referred to in fstab.

Thanks for any help

The **Seagate** reference is the *share name*.  The **james** reference is the *mount point* in the file system.  You can't really change the display.  It doesn't matter whether it is mounted via your CLI command or via the fstab command.

---

### Post by Impavidus on 2014-02-07
If you put something in /etc/fstab with the **noauto** option, Ubuntu doesn't try to mount it during boot, so it won't affect your boot time if the other computer is switched off. If you also add the **user** option any user can mount it, so you don't have to add sudo and give your password.

---

### Post by James Wilde on 2014-02-07
Thanks, Impavidus, I think I'll try that.

---

### Post by James Wilde on 2014-02-07
Thanks to all who made suggestions.  I'll test them, starting with Impavidus, which looks to be the best.

---


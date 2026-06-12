---
title: "Backup files after crash"
date: 2006-11-15
forum: General Help
---

### Post by ofir_k on 2006-11-15
Hello,

I use Ubuntu edgy. Last night when I installed some programs (beryl, xgl and nvidia drivers) Xorg crashed and I can't fix it.

Instead of trying to fix the problem, I decided to backup my files and format. But, I don't know how to backup my files without the GNOME's GUI.

If you know how to backup files using the command-line, please instruct me.

Regards,
Ofir

P.S
I have Samba network with Wondows XP and another Ubuntu Edgy. I can also burn the files into a cd ot copy them into USB Flash. (I just don't know how to do it without gui).

---

### Post by Ramses de Norre on 2006-11-15
Do you want to backup your whole system? If so:
```
sudo -s
cd /
tar -czf backup.tar.gz *
```
You can of course change / for /home/`whoami`/ to backup only your home folder and change backup.tar.gz to /media/.../backup.tar.gz to create the archive on a usb disk or something.

To extract:```
tar -xzf backup.tar.gz
```

(man tar for more info)

---

### Post by ofir_k on 2006-11-15
I can backup my files but I can't mount the usb disk. How I can mount the usb disk?

Regards,
Ofir

---

### Post by Ramses de Norre on 2006-11-15
Try to start up gnome-volume-manager, it may work without X or gnome and will automount then. Use mount to watch your mounted devices.

If that doesn't work:```
dmesg ##search for the /dev/??? for the usb drive
sudo mkdir /media/usb
sudo mount -t vfat -o utf8,umask=0000 /dev/??? /media/usb
sudo eject /media/usb ##at the end to unmount the usb drive
```

---

### Post by ofir_k on 2006-11-15
It works!!! I managed to mount the USB disk and backup my files. Now I just need to format and reinstall ubuntu and I done.

So...
1. Thanks Ramses de Norre for your help. :KS
2. For the "future generations", I will summarize the steps:
[COLOR="Red"]Before we start, run this:[/COLOR]
```
sudo -s
```
This should give you an admin permissions (see that instead your user name, it becomes "root". [user-name@computer-name...]).

**Step 1**
Enter your USB disk. When the system recognize it, the system will print some information about the USB disk to the screen.
**Step 2**
Run:
```

dmesg

```
In step 1, the system printed the name of the file that handles the USB disk. Try to compare that output to the last block from "dmesg".
For example:
```

[17285686.032000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17285686.032000] sdb: Write Protect is off
[17285686.032000] sdb: Mode Sense: 03 00 00 00
[17285686.032000] sdb: assuming drive cache: write through
[17285686.036000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17285686.040000] sdb: Write Protect is off
[17285686.040000] sdb: Mode Sense: 03 00 00 00
[17285686.040000] sdb: assuming drive cache: write through
[17285686.040000]  sdb: sdb1
[17285686.040000] sd 29:0:0:0: Attached scsi removable disk sdb
[17285686.040000] sd 29:0:0:0: Attached scsi generic sg2 type 0
[17285686.260000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
In the above output, all lines begin with "**sdb**" _**BUT**_ notice that in the fifth line from the end, "**sdb**" becomes "**[COLOR="Red"]sdb1[/COLOR]**".
Therefore, we will use sdb1 for our next steps.
**Step 3**
Mount the driver by typing these commands:
```

sudo mkdir /media/usb
sudo mount -t vfat -o utf8,umask=0000 /dev/sdb1 /media/usb

```
Notice: if in step 2, the system gave a different name for your USB disk, then replace "sdb1" in the code above with the one the system gave you.

If you have encountered a problem, try to type the above commands again and make sure that your spelling is correct.
**Step 4**
Now, "cd" to your dir and type the following command:
```

tar -czf /media/usb/backup.tar.gz *

```

After you are done, type:
```
eject /media/usb
```
And eject your USB disk.

Hope it helped you,
Ofir

---


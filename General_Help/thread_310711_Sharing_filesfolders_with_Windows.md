---
title: "Sharing files/folders with Windows"
date: 2006-12-01
forum: General Help
---

### Post by Infiltraitor on 2006-12-01
I want to get my music from windows without using an external device, which means through the computer. This is my first time doing it, is there a step-by-step guide dealing with this? I already have samba installed...

---

### Post by LLRNR on 2006-12-01
That shouldn't be any trouble at all... Have you already [mounted](http://psychocats.net/ubuntu/mountwindows) your Windows partition?

LLRNR

---

### Post by Infiltraitor on 2006-12-01
i have no idea what mounting is.

---

### Post by LLRNR on 2006-12-01
Have you looked at the orange thing above called LINK ????

---

### Post by Infiltraitor on 2006-12-01
I follow that guide, and input "fdisk -1" into the terminal... and get this:

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


So I have to do this mounting stuff before I start to share files with windows?

---

### Post by Bremen Saki on 2006-12-01
That's a lower-case letter "L", not the digit "1".

---

### Post by LLRNR on 2006-12-01
Bremen Saki beat me to it ! :D

Yes, the first time only. Just this time, come on :) After this mount you'll have permanent access to your Windows partition (read only though if the partition is a NTFS one).

LLRNR

---

### Post by Infiltraitor on 2006-12-01
I'm stuck at the 'fstab' part...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=614ed860-bb7c-47f9-b6ed-c1d7baac654e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=181a3e6b-024d-4833-a7d0-7e4b5acae7ba none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

All I know is that hda3 is the linux partition. (I do not see my windows partition, hda2) Other than that, I don't know what to do. And it's read only, so how can I edit?

Thanks for the ongoing help!

---

### Post by LLRNR on 2006-12-01
As mentioned in the guide, if you edit your fstab file using ```
sudo nano /etc/fstab
```you will be able to save it... see the " ^ " things in nano ? They stand for your Ctrl key, so just hit Ctrl+O to save when you're done (save = write out) and then Ctrl+X to exit.

Output for ```
sudo fdisk -l
```?

---

### Post by Infiltraitor on 2006-12-01
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         768     5806048+   b  W95 FAT32
/dev/hda2   *         769       13777    98348040    7  HPFS/NTFS
/dev/hda3           13778       15430    12496680   83  Linux
/dev/hda4           15431       15505      567000    f  W95 Ext'd (LBA)
/dev/hda5           15431       15505      566968+  82  Linux swap / Solaris

```
hda2 is windows.

---

### Post by LLRNR on 2006-12-01
```
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Add this line:```
/dev/hda2 /windows ntfs nls=utf8,umask=0222 0 0
```Save (Ctrl+O), confirm (enter), exit (Ctrl+X). Then:```
sudo mount -a
```You should then see your Windows partition in your filesystem, in the folder called "windows".

LLRNR

---

### Post by Infiltraitor on 2006-12-01
It worked!! Thanks man!!

---

### Post by LLRNR on 2006-12-01
> **Infiltraitor said:**
> It worked!! Thanks man!!

Thumbs up ;) Enjoy !

---

### Post by Infiltraitor on 2006-12-01
Is there any way to make that 'windows' folder a shortcut on the desktop?

---

### Post by LLRNR on 2006-12-01
> **Infiltraitor said:**
> Is there any way to make that 'windows' folder a shortcut on the desktop?

I forgot how to do it in Gnome, but it's basically the same as in KDE - once in your file browser (Nautilus I suppose), when you see the folder, you can drag it to the desktop and from the contextual menu that appears select "Link here" or whatever that sounds similar with "link" or "shortcut" (you wouldn't want to copy it, I think).

LLRNR

---

### Post by Peepsalot on 2006-12-01
> **Infiltraitor said:**
> Is there any way to make that 'windows' folder a shortcut on the desktop?

You can do it in a terminal like this:
```

cd ~/Desktop
ln -s /windows "Windows Partition"

```
You might need to press F5 to refresh your desktop to make the icon appear.

---

### Post by threegremlins on 2006-12-01
my option to to take back post, obviously problem solved

---


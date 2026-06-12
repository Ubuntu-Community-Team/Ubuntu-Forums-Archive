---
title: "Partition visible, but not loaded"
date: 2014-02-24
forum: General Help
---

### Post by Xanthius on 2014-02-24
I have this small issue with my ubuntu wich is hopefully easy to resolve, cause it's getting to be a nuisance and quite frankly I don't know what to search for in this case.

The issue is that the content of my partition is only being loaded when I click in the Files -> Devices -> "Storage" (name of partition).
Now for example, I boot up Steam the installed games pop up in the list and everything is fine and peacy.

However if I skip that step, I can either choose to install the game by selecting the correct directory and everything appears as installed or shutting down steam do the first step and boot it up again.
But it can be applied with everything, audacious playlist skipping files which are on the hdd, dash not searching the hdd by default, etc.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9849

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   120000511    59999232   83  Linux
/dev/sda2       120002558   234440703    57219073    5  Extended
/dev/sda5       120002560   127999999     3998720   82  Linux swap / Solaris
/dev/sda6       128002048   234440703    53219328   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   167979007    83886080    7  HPFS/NTFS/exFAT
/dev/sdb3       167979008   625141759   228581376   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003055b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  3907024895  1953511424    7  HPFS/NTFS/exFAT
```

My current setup, is sda = SSD, sdb = HDD.
sda1 = /
sda5 = Swap
sda6 = /home

sdb1 = windows recovery
sdb2 = windows install
sdb3 = ext4 "Storage" file system.

I've tried messing around in the "disks" application, which is currently on automount.
If I change those settings, I get an error before unity is loaded up saying with weird stuff or break it from mounting completely.
I read somewhere that that might have to do with ext4, not needing the extra args what ext3 requires.



Apart from this, I do have another issue in which I am willing to open up a new topic but if there is a quick fix I'm happy to hear.

I've messed around installing Gnome 3 (from omgubuntu) removed it and now the logout/shutdown screen shows the gnome loading logo instead of the unity one.
It's also causing some other minor issues, but nothing critical. I'd rather not reinstall but i'm guessing I might have no choice.

Thanks in advance.

---

### Post by coldcritter64 on 2014-02-24
Check the file /etc/fstab for what partitions are mounted at startup.
Mounting and mount options are set up with fstab for any partitions automatically loaded at startup.

Some further info [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Xanthius on 2014-02-24
Actually, I've tried that already which resulted in after login error messages. Also that guide does not explain for ext4.
But thanks to the keywords in your reply I've managed to search the answer.

I really wasn't sure if the drive was mounted, as it was just a second HDD. It could have just been merely enlisted.

But your where still correct. solution, Fstab ;)
In my case:
```
/dev/sdb3 /media/Storage ext4 default 0 0
```

I'm just not sure what I inserted last time

Thanks for the help
Best regards,

---

### Post by coldcritter64 on 2014-02-24
> **Xanthius said:**
> ...
```
/dev/sdb3 /media/Storage ext4 default 0 0
```....

Good entry, but I'd suggest you identify the partition in fstab by UUID=, not by its device allocation which can possibly change. If ever the boot order changes with "UUID=" classification the drive will still be found, by device it can be "lost".

If you wish to consider UUID identification, runnig the command below in a terminal will pick up the hardware identifier for the partition /dev/sdb3,
```
sudo blkid -c /dev/null /dev/sdb3
```

Edit fstab (gksudo gedit /etc/fstab)and alter your entry to
```
UUID=<insert-the-uuid-from-the-blkid-command-above> /media/Storage ext4 default 0 0
```
do not include the <> s above in your entry and ensure you don't copy any of the quotation marks that are displayed by the blkid command above. 

To test entries are OK, use the code
```
sudo mount -a
```better to have errors showing up in the terminal rather than at boot time.

Cheers, coldcritter64

PS. my fstab entries show "default" as "defaults", it *_may_* make a difference to your partitions mounting. My options are put in place by the installer.

---


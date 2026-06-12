---
title: "USB, Read only"
date: 2013-03-23
forum: General Help
---

### Post by unluckyclover on 2013-03-23
Hello.
Until a few days ago my usb was working perfectly. However recently it has refued to allow me access or to see its files with its explanation being that it is a read only file system. Is there a way to fix this without having to reformat?

---

### Post by lovevn on 2013-03-24
I don't know real problem but sometimes, my USB has similar problem. Suddenly, USB' files and folders are changed to read-only so I can't copy any things to USB. Then I reject USB and put it again. It done! I only have the experience for you.

---

### Post by Buntu Bunny on 2013-03-24
I had this problem awhile back, it happened after using the USB stick to look at some files with a Windows computer. After that it was read and write in Windows, but read only with Ubuntu. Never did figure it out so I hope you get a helpful answer for this.

---

### Post by badhorse on 2013-03-24
For a read-only USB try this:

Plug in the device and wait about 5 seconds

run in a terminal

dmesg | tail

If you see something like this:
FAT: Filesystem panic (dev sdh)
fat_get_cluster: invalid cluster chain (i_pos 0)
File system has been set read-only, then you probably have a munged file system. Make a note of the device name.

run

sudo dosfsck -av /dev/sdX

- replace X with your device name

When it finishes, unmount the device, unplug it, wait a few seconds, then plug it back in. If all went well you should now be back to rw mode. Check the device and make sure there are no .fsk files on the drive. If there are, just delete them.

---

### Post by unluckyclover on 2013-03-25
I entered the top command and got this:

james@james-desktop:~$ dmesg | tail
[30039.312215] sd 7:0:0:0: Attached scsi generic sg2 type 0
[30039.313534] sd 7:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[30039.314735] sd 7:0:0:0: [sdb] Write Protect is off
[30039.314739] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[30039.315480] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[30039.326945]  sdb: sdb1
[30039.330015] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[30040.074863] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[30040.074866] FAT-fs (sdb1): Filesystem has been set read-only
[30040.079813] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)

---

### Post by badhorse on 2013-03-27
Now run in a terminal:

sudo dosfsck -av /dev/sdX

- replace X with your device name (sdb in your case)

When it finishes, unmount the device, unplug it, wait a few seconds, then plug it back in. If all went well you should now be back to rw mode. Check the device and make sure there are no .fsk files on the drive. If there are, just delete them.

---

### Post by sudodus on 2013-03-27
It might also be possible to use ```
chkdsk /f
``` in Windows to repair the FAT32 file system, or use what is probably a GUI frontend to chkdsk in newer versions of Windows.

It is a good idea to use Windows tools to repair Windows file systems (FAT32 and NTFS).

---

### Post by unluckyclover on 2013-03-28
I managed to fix it by repairing it on a computer at my university. Thanks for the help everyone.

---

### Post by llamabr on 2013-03-28
To avoid, be sure that you eject the device before removing, rather than just yanking it out before you go.

---

### Post by raja.genupula on 2013-03-28
> **unluckyclover said:**
> I managed to fix it by repairing it on a computer at my university. Thanks for the help everyone.

We are very much glad that you have solved your issue and now please mark your thread as solved from thread tools.

---


---
title: "Unplugging USB pen drives without unmounting can damage them ??"
date: 2015-08-25
forum: General Help
---

### Post by arunb on 2015-08-25
Hi,

Can USB pen drives be damaged if they are simply unplugged instead of unmounting them first ??

I am designing a kiosk program that will run on Lubuntu OS, the program can detects USB pen drives inserted by users, there is an option for manually unmounting the drive, however most users have the habit if simply unplugging them, 

So will this damage the drives ?? make them unreadable, I know the powered USB external hard disks need to be un-mounted or ejected safely, but does this also apply to USB thumb drives as well ??

Fyi
I use the 'ls -laF /dev/disk/by-uuid' command to get list of drive inserted, then use the mount command to mount the drive, for un,mounting I use the umount command....


thanks
a

---

### Post by sudodus on 2015-08-25
Yes.

I don't think it will damage the hardware in the pendrive, but if the buffers are not flushed (written to the drive) before unplugging, ***the file system will probably be damaged***. Sometimes Testdisk can restore the file system. Some files might be possible to recover with PhotoRec even when Testdisk fails.

So it is very important that the users unmount the drive before unplugging. ***umount*** runs ***sync*** to flush the buffers before the actual unmounting.

If you can make the kiosk program run ```
sync
``` automatically (either at frequent intervals of time or whenever the computer is fairly idle) it would reduce the risk when unplugging without unmounting.

---

### Post by HermanAB on 2015-08-25
The problem is that memory schticks are usually formatted with the super simple FAT file system.  FAT doesn't have a journaling system that records intended actions before they are executed, thus allowing rollback.  If a file transfer is interrupted, then the FAT becomes out of sync with the actual files, which manifests as a corruption.  There is no solution for this.  Well, there is - don't use FAT - but that is sometimes not a viable option.

---

### Post by arunb on 2015-08-27
> **sudodus said:**
> Yes.

I don't think it will damage the hardware in the pendrive, but if the buffers are not flushed (written to the drive) before unplugging, ***the file system will probably be damaged***. Sometimes Testdisk can restore the file system. Some files might be possible to recover with PhotoRec even when Testdisk fails.

So it is very important that the users unmount the drive before unplugging. ***umount*** runs ***sync*** to flush the buffers before the actual unmounting.

If you can make the kiosk program run ```
sync
``` automatically (either at frequent intervals of time or whenever the computer is fairly idle) it would reduce the risk when unplugging without unmounting.


So I keep running sync after a set time ??

By damage I was thinking of a physical damage to the flash memory.

Also is there any way a SSD could be damaged by overwriting a file continuously every few seconds ?? I know flash memory writes are limited unlike hard disks, so I was thinking if the same applied to SSD ??

The kiosk PC I am using has a SSD, but I overwrite some files every 20 seconds, I hope this doesn't damage the drive ??

thanks
a

---

### Post by sudodus on 2015-08-27
Yes, I think SSDs have lower expected number of write cycles before damage than HDDs. SSDs are much better than USB pendrives, but still, yes, they wear when being written to. An alternative might be to use a RAM-drive and write to the SSD (or a HDD) when shutting down or rebooting. If you have enough RAM, you can try with the boot option **toram**.

An alternative is to try according to the following link

[Making Ubuntu Fast using RAM (updated and simplified)](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by nerdtron on 2015-08-27
> So I keep running sync after a set time ??
No, If you unmount/eject the drive safely (either the file manager or command line) the OS will issue sync automatically to write cache to disk and your data will be safe.

> By damage I was thinking of a physical damage to the flash memory.
I think damage is only on file system if you did not eject safely.

> Also is there any way a SSD could be damaged by overwriting a file  continuously every few seconds ?? I know flash memory writes are limited  unlike hard disks, so I was thinking if the same applied to SSD ??

The kiosk PC I am using has a SSD, but I overwrite some files every 20 seconds, I hope this doesn't damage the drive ??
SSDs nowadays have good read/write times. I think I saw SSDs with 5 year warranty (or more) on them. 5 years is a good run on hard drives, because you know, any hardware will eventually fail.

---

### Post by efflandt on 2015-08-27
I think the only thing that would normally corrupt USB memory is if it is unplugged "while" being written to. And people may not realize that it is slower than a normal drive or if it has finished, especially if it has no LED that blinks when it has activity. If it is not being written to I do not think unplugging it is a problem.

---


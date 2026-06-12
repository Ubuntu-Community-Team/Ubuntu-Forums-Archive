---
title: "Extracting Linux files onto other OSes?"
date: 2014-01-11
forum: General Help
---

### Post by BaffleBlend on 2014-01-11
My Lubuntu Live USB won't boot. Problem is, though, the most recent revision of my novel's saved onto there, so I need to figure out how to extract the files onto Windows so I can safely reinstall.

Problem is, though, no amount of googling will help. It always tries to tell me how to open Windows files on Linux, not the other way around.

---

### Post by devine.steve on 2014-01-11
what is the extention of the file you are trying to open?

---

### Post by BaffleBlend on 2014-01-11
.rtf is the extension of the file I'm trying to get to. But, it's buried and trapped in Linux's encryption.

Before you wonder why it's that instead of .odt or the like, I use Liquid Story Binder XE to write, so that's why.

EDIT: I THINK it's in a .squashfs, but I'm not entirely sure.

---

### Post by steeldriver on 2014-01-11
If you saved your document to your home directory on a live USB with persistence, then you should be able to recover them from another Linux system after mounting the casper-rw loop file

I'm not aware of any way to do that from Windows - can you burn a minimal Linux system to another USB or CD? Something like this --> [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

---

### Post by TheFu on 2014-01-11
If it is encrypted, I hope you have a backup.  If you do NOT have a backup, then a Linux system will be needed to access the encrypted data.

if it is not really "encrypted" (where you joking?), just stored on a normal EXT4 partition, then use a live-CD of Ubuntu and you can point-n-click to access the HDD storage and will find the files were you expect them to be.

So, if encrypted - please be clear how that happened and which sort of encryption is involved.

---

### Post by BaffleBlend on 2014-01-11
> **steeldriver said:**
> If you saved your document to your home directory on a live USB with persistence, then you should be able to recover them from another Linux system after mounting the casper-rw loop file

I'm not aware of any way to do that from Windows - can you burn a minimal Linux system to another USB or CD? Something like this --> [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

...er... I can try, I guess, although I'm not entirely sure I understand. I have an old laptop partitioned with Lubuntu that I can try, but it's been suffering some issues lately, too.

*sigh* Still, though, an ideal situation would be free-access to the files from any computer. I only use Linux when I absolutely have to because I just don't find it user-friendly at all, so bear with me because I'm most definitely going to sound like an idiot.

> **TheFu said:**
> If it is encrypted, I hope you have a backup. If not, a Linux system will be needed to access the encrypted data.

if it is not really "encrypted" (where you joking?), just stored on a normal EXT4 partition, then use a live-CD of Ubuntu and you can point-n-click to access the HDD storage and will find the files were you expect them to be.

So, if encrypted - please be clear how that happened and which sort of encryption is involved.

I'm not entirely sure if it's truly encrypted or not... I don't know how it works.

---

### Post by BaffleBlend on 2014-01-11
**UPDATE: **I currently have Lubuntu open in a virtual machine, and the flash drive is mounted and open in the file manager. So... now what?

---

### Post by The Cog on 2014-01-11
What partitions are there on the drive? Have a look with 
```
sudo parted -l
```

---

### Post by BaffleBlend on 2014-01-11
Gimme' a second, I'll type it in because it won't let me copy...

Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 15.6 GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number | Start  | End        | Size     | Type   | File system | Flags
1         | 1049kb|15.6GB    | 15.6GB | primary | fat32         |  boot, lba

Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

Error: /dev/zram0: unrecognised disk label

---

### Post by TheFu on 2014-01-11
> **BaffleBlend said:**
> I'm not entirely sure if it's truly encrypted or not... I don't know how it works.

If you didn't choose to encrypt anything, then it is NOT encrypted.  With much respect to the other advice provided so far, the easiest way to get your files is to boot off a live-CD of Ubuntu (or whatever Linux-OS you normally use), then use the file manager to access the HDD inside the PC. It should be THAT easy.

Using a virtual machine will be more effort and more complex.

Just use almost any Linux with a GUI Liveboot CD and access the files.

---

### Post by BaffleBlend on 2014-01-11
> **TheFu said:**
> If you didn't choose to encrypt anything, then it is NOT encrypted.  With much respect to the other advice provided so far, the easiest way to get your files is to boot off a live-CD of Ubuntu (or whatever Linux-OS you normally use), then use the file manager to access the HDD inside the PC. It should be THAT easy.

Using a virtual machine will be more effort and more complex.

Just use almost any Linux with a GUI Liveboot CD and access the files.
So... are you saying I should use a Live CD to access my Live USB?

---

### Post by ajgreeny on 2014-01-11
> **BaffleBlend said:**
> So... are you saying I should use a Live CD to access my Live USB?

You could do that quite easily if you have no installed *ubuntu OS to use.

Boot to a *ubuntu OS (real or live system) and attach the faulty live USB.

Use command ```
sudo mount -o loop /media/*pendrive*/casper-rw  /mnt
```  (Replace "*pendrive*" with the mount directory of your pendrive).

This means that files saved to your live OS should now be mounted and available at /mnt/home/ubuntu/Desktop/

If using a fully installed system save the files from the mounted folder to somewhere permanent, if on a live system you will have to save to another flash drive.

Don't forget to UNMOUNT when done!
sudo umount /mnt

---

### Post by steeldriver on 2014-01-11
*nevermind - ajgreeny got it covered*

---

### Post by BaffleBlend on 2014-01-11
EDIT: Never mind, I misread.

---

### Post by BaffleBlend on 2014-01-11
EDIT:l Never mind, I did something wrong. It works now... thanks for being patient with a stupid Windows user like me.

---

### Post by BaffleBlend on 2014-01-11
...except now I can't find where it's mounted TO.

EDIT: Never mind that, either - I got lucky stumbling on it, and my files are all safe. Thank you all so much.

---


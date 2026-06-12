---
title: "Write to Windows USB Hard Drive"
date: 2006-10-18
forum: General Help
---

### Post by th3gh05t on 2006-10-18
Hi, 

I have a USB adapter thing that connects to a tiny 2.5" hard drive from a laptop. When I connect it to a Windows XP machine, I can delete and move files to and from it.

But when I connect it to my Ubuntu box, I can only read files. I can't delete or move any files onto this hard drive.

How do I make this hard drive have permissions so that I can move files onto it?

Also, how do I ensure that I can still use this drive in Windows XP?

Thanks, th3gh05t

---

### Post by kidders on 2006-10-18
What filesystem is it using?

---

### Post by lmandrake on 2006-10-18
Make sure you are using FAT32 as filesystem and not NTFS because NTFS is not fully writable under Linux.

If you don't have the permissions do onetime a "sudo chmod 777 /media/whereeverthedriveis" when the drive is mounted

---

### Post by kidders on 2006-10-18
> **lmandrake said:**
> If you don't have the permissions do onetime a "sudo chmod 777 /media/whereeverthedriveis" when the drive is mounted

Since FAT32 doesn't have any kind of permissions support, this may not work on a permanent basis ... or at all. Assuming you're using FAT32 on your external drive, you should check out the **umask**, **uid** and **gid** mount options, so things work more "normally" every time you mount the device.

Filesystems that don't support permissions properly are a pain :-(

---

### Post by th3gh05t on 2006-10-18
Both partitions on the hard drive are NTFS.

Does this change what I type in?

---

### Post by kidders on 2006-10-18
Hmmm. You can write to NTFS with Linux if you really want to, but I wouldn't recommend it. Microsoft is too secretive to tell anyone how NTFS works, and Linux devs haven't managed to _reliably_ reverse-engineer it yet afaik :-(

> Does this change what I type in?
All the above suggestions apply to FAT32, which you *can* write to safely.

---

### Post by th3gh05t on 2006-10-18
Hi, 

So I should hook this up to a Windows box, and re-format the drives in FAT32?

Thanks, th3gh05t

---

### Post by kidders on 2006-10-18
If you're going to the trouble of reformatting your drive, you might as well switch to something better than FAT32!! I'm not sure about ReiserFS, JFS, etc., but you *can* teach Windoze to read the extended filesystems.

FAT32 is pretty diabolical, as filesystems go.

---


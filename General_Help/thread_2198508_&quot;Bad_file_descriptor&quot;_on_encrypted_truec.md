---
title: "&quot;Bad file descriptor&quot; on encrypted truecrypt volume"
date: 2014-01-09
forum: General Help
---

### Post by stefbeukers on 2014-01-09
Hi,

I'm having an encrypted volume (created by truecrypt) on my laptop. Everything worked fine, but now there's an error. "Bad file descriptor". I can't mount my volume, although my password is correct. I'm sure of that. 

 I have clearly no I idea where it is coming from, because I think I didn't change a thing. 

Any help on this one?

---

### Post by TheFu on 2014-01-09
Got a good backup?   Sorry, I am not any help. 

[Using encryption]("http://blog.jdpfu.com/2013/11/14/encryption-means-great-backups-needed") means giving up the ability for most disk tools to recover anything.  Something like **ddrescue** might get most of the data to another device (still encrypted), but if there is damage to critical parts of the file system, not much can be done.

Backups. The lowly, forgotten, backup is what you need.

---

### Post by stefbeukers on 2014-01-09
Yeah, I have backups. So I deleted my encrypted volume and created another new one. But when I try to mount this volume, I keep getting the same error.

---

### Post by Dave_L on 2014-01-09
What file system did you specify when creating the volume?

---

### Post by stefbeukers on 2014-01-09
FAT, it worked before. Since a few days I am getting this error.

---

### Post by Dave_L on 2014-01-09
Strange. I've been using Truecrypt for years, and have never seem that problem.

If you run fsck, does it indicate any issues?

Did you unmount the Truecrypt volume last time you accessed it?

---

### Post by TheFu on 2014-01-09
> **stefbeukers said:**
> Yeah, I have backups. So I deleted my encrypted volume and created another new one. But when I try to mount this volume, I keep getting the same error.

FAT?  Why?  There are stupid limits with FAT.  Heck, even NTFS would be better, though ext4 would be even better. ;) After all, supporting UNIX-file/owner/group permissions is an important part of file systems under Linux.

I'd do a surface scan of the partition to give the hardware a chance to self-fix. 
Is this a file-based volume or an entire partition?
Does creating a non-encrypted partition on the same storage work without any issues?  Could be just a bad sector on the HDD.  If the SMART data shows it as just a few, then the sector should get automatically located by the HDD. I don't think encryption should matter for that, but ... 

I'm of the opinion that when anything like this happens with a HDD, it is time to swap it out and relegate the problem HDD to backup duty only.  If something similar happens again on a different disk, check the controller and cable. I doesn't sound like those are the issue based on your description.

I might start having a 2nd backup, just in-case too.

---

### Post by stefbeukers on 2014-01-09
fsck doesn't find any issues. And I'm not sure if I did unmount it, but I've created a new one. The new one hasn't mounted once, so the unmounting problem can't be the thing here.

---

### Post by Dave_L on 2014-01-09
You could try asking about this on the Truecrypt forum: [http://forums.truecrypt.org/](http://forums.truecrypt.org/)
or using their contact form: [http://www.truecrypt.org/contact](http://www.truecrypt.org/contact)

But I would first do some more diagnosics (disk, memory, etc.)

---

### Post by stefbeukers on 2014-01-10
How do I do some of those diagnostics?

---

### Post by Dave_L on 2014-01-12
If I recall correctly, there's a memory test that you can select from the grub menu when booting.

I would run fsck with these options: -fnv
The partition you're testing should be **unmounted**.

To do a more extensive disk check, you can add the -c (check for bad blocks) option with fsck. That can take a long time to run.  If your disk is really starting to fail, this could accelerate the failure, so make sure everything is **backed up** first.

There are also GUI applications available for system testing, but with all the different desktop environments in use, it's hard to give specific information on how to do that.

---


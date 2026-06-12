---
title: "Hard drive not showing files"
date: 2016-02-02
forum: General Help
---

### Post by jsleotti on 2016-02-02
Hello, I'm on Ubuntu 14.04 and use an external hard drive for most all my stuff. Today, I plug it in like normal and, at first, it doesn't mount. When it does, it doesn't show any of my files in the only folder I really use, but in all others, it does. If I write a file to it, it works anywhere except that one folder. But it says 300gb are used of 1tb so it's obvious they're still there. If I look under folder access it says I have none. What could have caused this to happen and how can I fix it?

---

### Post by Vladlenin5000 on 2016-02-02
If your external HDD is NTFS then I suggest you plug it in a Windows system and do the usual error correction with the native Windows tools because it looks like file system corruption and the (Windows proprietary) NTFS partitions are better corrected in Windows.
If not NTFS please inform.

---

### Post by jsleotti on 2016-02-02
It should be. It says Master Boot Record under disks. I didn't reformat it when I bought it so it's safe to assume that it is. I'll give it a try tomorrow.

---

### Post by Nuno_Abreu on 2016-02-03
Probably your external hard drive is dying. What is the output of this:
```
sudo blkid
```

---

### Post by jsleotti on 2016-02-03
I can't imagine it's dying since I've had it for only like 2 months. If it is, that's a really short lifespan.

Having plugged it into Windows, it said the destination is corrupted and unreadable. I clicked scan and repair and now I can see them all. I'm going to back them up on this computer just to make sure. I kind of wish there was a way to do this is Linux though, especially since I'm think of getting rid of my Windows and switching to Mac.

---

### Post by yancek on 2016-02-03
It's a windows filesystem which is proprietary and as such it is extremely unlikely that you can run a filesystem check from Linux.  It's amazing that different developers were able to write software to be able to access and read/write to windows filesystems.

---


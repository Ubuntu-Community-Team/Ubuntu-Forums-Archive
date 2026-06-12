---
title: "Give Permission For Drives"
date: 2007-08-08
forum: General Help
---

### Post by iAndrew on 2007-08-08
Hi, on my system I have a Windows XP / Ubuntu 7.04 Dual Boot.

I have 2 drives, a 320 gb, and a 80gb.

I partitioned the 320 gb, and it **does show up in ubuntu**.

I can read, but I'd like to learn how to set it so I can also write to the drive. Is that possible?

---

### Post by forestpixie on 2007-08-08
I assume it's an NTFS drive - you can install ntfs-3g and ntfs-config to allow write to NTFS drive, you can read about it here

```
http://www.ntfs-3g.org/index.html
```

To install in a terminal 

```
sudo apt-get install ntfs-config
```

once it's installed, you'll get a tool in Apps > System Tools. You'll need to reboot I believe.

---

### Post by iAndrew on 2007-08-08
Oh I slept after this post, thanks alot. I'll try it out.

---

### Post by iAndrew on 2007-08-08
Worked great. Thanks alot dude.

---


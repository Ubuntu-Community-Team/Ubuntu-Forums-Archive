---
title: "Hard Drive Permission and Nero, XMMS, Brasero, etc."
date: 2007-02-28
forum: General Help
---

### Post by Nemix77 on 2007-02-28
Hi, this my first thread in the Ubunutu Community Forums.  I'm gonna take this time and say thanks to all those for making easy to follow guides on virtually anything Ubuntu related. 

I've got Windows XP and Ubuntu 6.10 dual booting off the same hard drive in separate partitions.  I've  also got 2 other hard drives NTSF format with my files, I'm using NTFS-3G  to read/write from the NTFS drives.  Ubuntu recognizes my NTFS drives fine and I also able to read/write fine too. 


Now my problem, when I load programs that I need  or want to access to my other drives (NTFS), it doesn't allow me to access them.  To put into better words, I can't see the drives at all through these type of programs (Nero, XMMS, Brasero, etc.)  Another weird thing is I can see my drives through Nautilus (Desktop Computer Icon) but can't access or see the drives when running Nautilus as ROOT.

This is the message I got from Nero at startup: 

Some of your drives are not accessible.  Please check that you have the correct permission on the corresponding device files.

Any help thanks,

---

### Post by Nemix77 on 2007-02-28
got it sorted out thanks,

---

### Post by zvacet on 2007-02-28
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite")

---

### Post by Nemix77 on 2007-02-28
Thx, so I was getting it all wrong! nero did see my drives but it was running with ROOT privileges, so my files were placed in /media/hard drive, where as the desktop Computer icon not running in ROOT shows me my hard drive icons.  I would rather nero and other programs show me seperate hard drive places though and here I went and made another EXT3 partition and copied all the files I needed form my NTFS partitions to it.  :lolflag: 

Thnx.

---


---
title: "Filesystem mounted but not displayed in Places Menu"
date: 2007-03-23
forum: General Help
---

### Post by spivak.d on 2007-03-23
Hi all,

I've edited by fstab recently to automatically mount a Windows NTFS partition on my laptop using ntfs-3g as well as a FAT32 partition that would be a common email drop spot from both Windows and Ubuntu; my additions appear below:

```

/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda2 /media/Email vfat iocharset=utf8,umask=000  0    0

```

As it stands, my problem is two fold:

1) While this command mounts my Windows partition to /media/Windows, the partition appears neither in Ubuntu's Places menu nor in Nautilus under "Computer;" I have to actually go to /media/Windows to use it.

2) While I've relabeled it several times, my Email partition will refer to itself only as EMAIL and not Email, as I'd prefer. Any way to change this capitalization?

Sincerely,
Dima

---

### Post by raja on 2007-03-23
For problem 1, you navigate to the folder in Nautilus and bookmark it. It should then appear in the places menu. Sorry, I dont know why you are having the second problem.

---

### Post by zorkerz on 2007-03-25
This may be similar to my problem. My music partition shows up as music and also MUSIC. The later shows up on the desktop but cannot be mounted. 
fstab > # Entry for /dev/hda2 :
UUID=4454-68F0 /media/music vfat umask=000 0 0
any ideas?

---


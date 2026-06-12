---
title: "CAPITAL letters on VFAT/FAT32 Partition"
date: 2007-07-14
forum: General Help
---

### Post by wizzkid on 2007-07-14
Hi Guys,

I have the latest ubuntu running on my machine. I partition my drive so I can dual boot windows xp. Now I have FAT32 partition to share with WindowsXP and Ubuntu, all went well expect that when Im working on linux and I create a filename with ALL CAPITAL LETTERS on FAT32 partition, ubuntu change it to all small letters. ex. when I create file called HELLO it will become hello. 

I need to createee ALL CAPITAL Letters on FAT32, since my Thunderbird email client' inbox file is in all capital letters...

Here's my FAT32 line on FSTAB 
UUID=447B-0C43 /media/data vfat user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850 0 0


Hope you could help me on this matter!

Many Thanks.

---

### Post by ldrn on 2007-07-14
Sure! You need to change that line on your fstab to read:
```
UUID=447B-0C43 /media/data vfat shortname=winnt,user,auto,gid=100,uid=1000,umask=002,iocharset=utf 8,codepage=850 0 0
```

If that doesn't work, you could also try:```

UUID=447B-0C43 /media/data vfat shortname=win95,user,auto,gid=100,uid=1000,umask=002,iocharset=utf 8,codepage=850 0 0
```

---


---
title: "How to free more hard disk space?"
date: 2018-04-24
forum: General Help
---

### Post by christon74 on 2018-04-24
Good morning fellow Ubunters :) 
Ubuntu Flavour : 16.04 LTS
Memory: 6.5 GiB
Processor inter core duo CPU E 7500 @2.93 Ghz x2
Graphics: llvmpipe (LLVM 5.0, 128 bits _ OS type : 64 bits
Disk: 131.7 GiB (118 used)

I have tried bleach, I have updated, I have removed old kernels. What more can I do? 
I am on dual boot (Windows7/ Ubuntu). What if I try shrinking the windows partition with disk management? Can it help?
Thanks.

---

### Post by vanadium on 2018-04-24
Move some of your documents/movies/audio to an external drive. Your Ubuntu operating system only takes about 12 GB, so there is not much to be gained there.

---

### Post by christon74 on 2018-04-24
Yes, I have already done that. I have also removed Openshot video which is quite heavy, as well as other softwares I hardly ever use like EasyTag. Still, this does not really offers more free space. After removing many video files, I can still see 118 GiB used. Anyway, thanks for the tip. ;)

---

### Post by dragonfly41 on 2018-04-24
To inspect disk usage .. install **duc** ..

then run the command

duc gui

or if inspecting a folder such as /var

duc gui /var

---

### Post by uRock on 2018-04-24
/var is a great place to look. /var/log may have some large log files in it.  Have you run Bleachbit as root? Be careful what you select as I have seen some complain of it causing issues. I have included a screenshot of what I select in Bleachbit as root.

---

### Post by christon74 on 2018-04-25
Good morning and Thanks to both of you Urock and Dragonfly ;). I will try using Bleach as root, and see what duc does.

---

### Post by christon74 on 2018-04-26
Hey, hey, I have found out what is taking so much space on my hard disk! It's the backup files which are usually saved to deja-dup. I have deleted some dating back to March 2nd and have thus freed a considerable amount of disk space!

---

### Post by monkeybrain20122 on 2018-04-26
> **christon74 said:**
> Yes, I have already done that. I have also removed Openshot video which is quite heavy, as well as other softwares I hardly ever use like EasyTag. Still, this does not really offers more free space. After removing many video files, I can still see 118 GiB used. Anyway, thanks for the tip. ;)

Openshot is just one file, you can download it as an [appimage]("https://www.openshot.org/download/") 139 mb, easytag is probably only a few kb.

---


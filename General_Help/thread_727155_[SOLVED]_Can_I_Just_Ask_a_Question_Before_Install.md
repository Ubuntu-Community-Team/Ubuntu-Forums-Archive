---
title: "[SOLVED] Can I Just Ask a Question Before Install"
date: 2008-03-17
forum: General Help
---

### Post by OllyNewport on 2008-03-17
Ok, right before I install I would just like to ask a question to all of the people out there.

I have a Windows XP Home SP2 -  AMD64 Turion 1.8Ghz pc with 1GB RAM and ATI RADEON XPRESS 200M Graphics.

My question is, I have to partitioned HDD's, one is 80GB and has my windows xp install on, the second partiton I have is 10GB, and I created it for free space & other things.

Now that I could install Wubi on the 10GB free space partitioned drive, do you think that it would muck the install up, if it isn't on the 80GB drive?

Just would like to know, thanks!

---

### Post by ago on 2008-03-17
Provided the partitionn is formatted as ntfs wubi will run happily there (wubi 8.04 is recommended at this point. 7.04 will be replaced soon.), but since you already have a dedicated partition you might just as well do a full installation in there... 

The main difference is that in the second case the bootloader gets replaced (with a better one...) but you have a more robust filesystem, can hibernate and get better disk performance.

---

### Post by OllyNewport on 2008-03-17
Thanks for that, also would it be possable to change the Wubi ISO image that you download from ubuntu-7.04-alternate.iso to ubuntu-7.10-alternate-amd64.iso?

Sorry, but I haven't used these sort's of installers before, and I have to be careful because something went wrong last time with my other computer.

Thanks!

---

### Post by ago on 2008-03-17
> **OllyNewport said:**
> Thanks for that, also would it be possable to change the Wubi ISO image that you download from ubuntu-7.04-alternate.iso to ubuntu-7.10-alternate-amd64.iso?

Wubi 8.04 (recommended) requires an 8.04 DESKTOP ISO, it will download the ISO for you or you can download it yourself and place it in the same folder: 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---


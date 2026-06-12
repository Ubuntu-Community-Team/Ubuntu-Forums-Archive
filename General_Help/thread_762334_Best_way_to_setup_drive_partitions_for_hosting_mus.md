---
title: "Best way to setup drive partitions for hosting music and shared media?"
date: 2008-04-22
forum: General Help
---

### Post by jd@smokin-barrel.com on 2008-04-22
Hi all,
  I am planning on building a new home pc which will serve as the music/media server for the house.  It will be ubuntu, but will also have windows xp running in VMWare.  I would like to setup a large partition dedicated to media and music, but since we will be ripping hundreds of cd's into flac, I dont want to lose this data or store it more places than 1.  So I want to setup the drive so that it can easily be used by different OS's and still be in tact if i somehow destroy the original ubuntu install. 

What is the best way to do this?  I have never messed with linux partitions, except for messing with it during install.  Should i just install the OS, then do the partition after the fact?  If so, how?  NTFS?  

Thanks,
JD

---

### Post by jd@smokin-barrel.com on 2008-04-22
I was wondering if I needed to include more info as I got no replies?  Please advise.

Thanks,
JD

---

### Post by RainCT on 2008-04-22
If you will mainly use GNU/Linux on that system, I'd say go for ext2/ext3; there is a program which adds support for them to Windows, so there shouldn't really be a problem if later you have to access it from The Other System.

---


---
title: "How do I get my raid 0 back"
date: 2007-01-27
forum: General Help
---

### Post by technoplume on 2007-01-27
Hi

    I have windows xp, and a partition on my raid 0 array. I can't acces it in linux and I'm looking for a way to get this array online. The windows partition I don't realy care what happen to it in the process. But the other partition as about 60gi of data I would like to keep an acess whit linux.

So I have 2 wester digital of 40gi in a RAID 0 config. Thewindows partition is about 20 gi and in NTFS. The Othe 60gi partition is in fat32.

the device manage can see both disk and list 2 volume
/dev/hde1
/dev/hde2

I tried to had the following to the stab file
/dev/hde2 /media/hde2 vfat umask=0000 0 0

but the partition does not appread after reboot.

---


---
title: "big problems after partitioning blocked"
date: 2007-03-16
forum: General Help
---

### Post by laurensH on 2007-03-16
hello,

i ve been using ubuntu in a dual boot with windows xp home for a couple of weeks now, everything worked fine until today...
i wanted to use free space from my windows partition to create a new partition in FAT32 format to put my audio and video files, so i can use them in both linux and windows.
i first used diskeeper to defragment, then partition magic to first make my c partition smaller and create some unallocated space. this is where things started to go wrong. when i rebooted and partition magic opened, it blocked at about 30 percent. i had to do a hard reboot, and sure enough, windows doesnt load anymore.
luckily, i still had ubuntu. there, it also didnt want to mount my windows partition. i looked around on some fora, and discovered TestDrive. this analyzed my drives (i could see my data were still on my NTFS partition), and said the number of head per cylinder (?) are wrong. it was 16 and it said i should change it to 255. i did this, had to reboot, and now grub doesnt load anymore. it says error 22.
the only way i can use my computer now is with an ubuntu liveCD, if i try to mount my hard disk it fails...

can someone who knows what he or she is doing (contrary to me) please help me? please keep in mind i am a complete newbie...
thanks a lot!

grtz

---


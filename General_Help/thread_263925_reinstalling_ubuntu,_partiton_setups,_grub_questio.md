---
title: "reinstalling ubuntu, partiton setups, grub questions"
date: 2006-09-23
forum: General Help
---

### Post by Polygon on 2006-09-23
Ok so i screwed up my hard drive (corrupted the filesystem... not fun) and im going to reinstall both windows and ubuntu to ensure that i will not have to go through a week of hell trying to fix everything again.

so... i have some question.

first off, im planning to make a seprate partiton for /home this time, is there any other partitions i should consider making besides the obvious / , /swap and /boot ? And how big should i make the / partiton? I have a 40 gb drive that ubuntu is going on.

second off, i have two hard drives, one that holds windows and one that holds ubuntu. I dont want grub to be erased every time i reinstall windows (which is often), so will making my ubuntu drive have grub and be the master drive and having windows as the slave drive, will that make it so that grub always stays intact and i wont have to reinstall it or the /boot partiton when i reinstall windows?

sorry if im repeating some commonly created posts, but the ones i searched for were kinda old.

thanks

---

### Post by wieman01 on 2006-09-23
Let me help you with question no. 1. I would create 4 partitions for Ubuntu:
> /[swap] : 2 x RAM (hda1)
/home : 5 GB (hda2)
/[root] : 10 GB (hda3)
/data : remaining space
I usually prefer to have my data & personal files on a separate partition. It easier this way if you need to backup and stuff. But I won't recommend any other partitions apart from those as I don't think you'd gain anything out of making it more complicated than it is. :-)

---

### Post by Polygon on 2006-09-24
ok, thanks. i take it that /data is your personal files while /home is all your config files and whatever else gets put there, correct?

and still want confirmation on the grub/hard drive question :D

---

### Post by wieman01 on 2006-09-24
> **Polygon said:**
> ok, thanks. i take it that /data is your personal files while /home is all your config files and whatever else gets put there, correct?
Yes, that's right.

---


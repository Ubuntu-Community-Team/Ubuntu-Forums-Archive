---
title: "Partitions Formatting FROZEN"
date: 2008-05-13
forum: General Help
---

### Post by iheartubuntu on 2008-05-13
My sister has a new laptop with Ubuntu 7.10 installed. I put World of Warcraft on the computer for her. She complained after installing WoW that her Ubuntu computer would freeze and lock up periodically. I decided to just do a fresh Ubuntu install, but now when trying to reinstall the Ubuntu OS (7.10 64bit - yes, its the correct one) and am at the formatting of the drive/partitions, when its creating the ext3 file system the computer hangs at 33%. Its been like this for over an hour now. Ive never experienced this prob before.

Any tips how to fix this? I also tried the 64 bit version of 8.04 which did the same thing. Im using ALT disc for 7.10 and the regular LiveCD for the 8.04.

Thanks for any help.

---

### Post by Wandering on 2008-05-13
You might want to select Manual Install and delete the original partition in which Ubuntu was installed. Then create a new partition, and set it as EXt3 and the file system root as /  (just the forward slash). It should install fine from there.

Good luck.

---

### Post by iheartubuntu on 2008-05-14
Hey thanks. It turned out to be a corrupted 2GB ram chip. I took it out and Ubuntu installed just fine.

---

### Post by The Pinny Parlour on 2010-02-16
Having the same problem... fresh install get stuck at partitions formatting 33%.

Tried different HDD's, 2 optical drives, 4 sticks of RAM, different SATA cable, disconnect floppy. Have tried  both normal and alt cd images using different burn speeds.

System was working with WinXP prior to this.

Any help would be great.

Thanks

---


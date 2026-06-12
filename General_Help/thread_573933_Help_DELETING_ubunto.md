---
title: "Help DELETING ubunto"
date: 2007-10-12
forum: General Help
---

### Post by chris670 on 2007-10-12
how do i do it?

i want to go back to windows..

---

### Post by swisscow on 2007-10-12
Depends on how you installed it - if you just installed Ubuntu over windows then do the opposite. If you have set up a dual boot you need to format the ubuntu partition(s) to let Windows use the space again (as FAT32????)

Having never done this I can't tell you exactly but there are plenty of threads on this forum on how to do it.

---

### Post by chris670 on 2007-10-12
i installed it on a separate hard drive (D:)

---

### Post by chris670 on 2007-10-12
how do i format the ubunto partitions, i cant see the drive ubunto is installed on through windows?

---

### Post by swisscow on 2007-10-12
Good plan - seperate drive.

Boot from the livecd, run gparted (partition editor) and format the partition into a format windows recognises - FAT32, NTFS, ......not so sure which  - it's been a while.

If gparted isn't on the livecd, you can get a rescuelivecd from 
[HTML]
http://www.sysresccd.org/Main_Page
[/HTML]

download and burn the iso just like for ubuntu.

Boot from it then you run the partition program and then go from there.

Don't know if there is an equivalent windows version

---


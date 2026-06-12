---
title: "Inluence of filesystem type. You should know."
date: 2023-02-15
forum: General Help
---

### Post by georgesgiralt on 2023-02-15
Hello,
I'm a long time user of Linux (and various Unix variants during my career). So I do regular backups of my computer (running Ubuntu) using dump.
Last week, I bought a new external disk of huge capacity in order to complement the external disk I use since long ago... 
I wanted to test it as soon as unpacked. So I plugged it in and made a huge dump (around 630 GB size) on it. The disk was ExFAT formatted to comply with the intended users : Windows and MacOS.
This huge dump took 3 hours to complete so not so bad performance ! (around 60 000 kB/s)
Reassured the drive was fine and fast, I formatted it with Ext4 file system as it will be used solely on Linux based computers. 
And of course, I had to make again the same backup to comply with my scheme of backups. 
This time, the 630 GB dump took ...... only..... a little more than ONE hour. so a third of the previous speed... (around 165 000 kB/s)
Same external disk, same computer, same USB port, same source same destination. Only difference : the file system on the external disk. !
So if you are wanting performance under Linux, IMHO, choose a native file system for your disk... 
Just my 2¢
Have a bright and nice day.

P.S. : I know that ExFAT support is not rock solid under Linux but I bet, that if the disk had been formatted using NTFS results won't have been that different...

---


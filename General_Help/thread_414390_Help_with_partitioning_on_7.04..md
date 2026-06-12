---
title: "Help with partitioning on 7.04."
date: 2007-04-19
forum: General Help
---

### Post by burritomaster on 2007-04-19
I have allocated a swap drive and a Linux partition. I know they work because I was dual booting 6.10 and XP before. But now when I was trying to install 7.04 It gives me a message saying "No root file system was defined. Please speak noob. Just wanted to say that this is a huge improvement from 6.10 because my wireless was automatically detected and my ATI card is putting out my native 1680x1050.

---

### Post by bwhite82 on 2007-04-19
Hello, in the partition manager you need to set whichever partition you're installing Ubuntu onto, to "root" or more technically, the option will be "/".

---

### Post by burritomaster on 2007-04-19
You mean where it says mount point because I really don't want to mess everything up.

---

### Post by bwhite82 on 2007-04-19
Yes. You won't mess anything up, just make SURE that it is your old Ubuntu partition that you are formatting and not your windows partition. In other words, leave the partitions that say "NTFS" or "VFAT" or "FAT32" alone and you should be fine.

---

### Post by burritomaster on 2007-04-19
Thank you very much. This worked great. Its installing right now.

---


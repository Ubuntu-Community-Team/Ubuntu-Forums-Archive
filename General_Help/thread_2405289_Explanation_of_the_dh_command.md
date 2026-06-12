---
title: "Explanation of the dh command"
date: 2018-11-03
forum: General Help
---

### Post by hrddrivinokc on 2018-11-03
When I execute the dh command in terminal, the attached output is created (screenshot).  I have looked and searched for what all of it means.  I was expecting it to list the available drives on my system, which it does at the end, but what in the world are the dev/loop(s), tmpfs, which are mounted.  I have tried to access these "drives", but have not found a way to do that.

As I am new to ubuntu.. is this normal system background tasks creating this for the system?  fyi-I just installed ubuntu, first time new, approx 1 week ago, and have been learning everything I can, focusing on basic tutorials.  This info is not shown in the file manager.  

If this is normal, please let me know, and I will mark as solved.   I appreciate your input, and am excited to be learning a new os.  thank you.

[IMG]/home/tlppgh/Pictures/Link to Screenshot.jpeg[/IMG]

---

### Post by Holger_Gehrke on 2018-11-04
Actually that's not 'dh' (which would be a helper for creating .deb package files), it's 'df -h' (**d**isk **f**ree, with **h**uman-readable units). The /dev/loop* entries are loop-devices, virtual drives used to mount image-files. snap packages are installed that way. The lines starting with tmpfs are ram disks, they only use as much space in RAM as is actually used, up to a configurable maximum). And udev is another pseudo file system on which automatically created device files reside. All quite normal.

BTW, you could free up about 500 M by removing the old versions of chromium and obs-studio ('snap remove --revision 494 chrome' and so on ...). If the current version works there's no need to keep the old version hanging around.

Holger

---


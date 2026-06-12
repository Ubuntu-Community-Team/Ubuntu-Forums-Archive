---
title: "/home partition problem"
date: 2007-04-09
forum: General Help
---

### Post by bubzilla on 2007-04-09
I just used [Psychocats guide]("http://www.psychocats.net/ubuntu/separatehome") to repartition and shift my /home to the new /dev/hda7 partition. All of my files appeared to copy over correctly, and I backed up my old /home as /home_backup and mounted the new partition to /home. Problem is, none of my setting transferred over. My video files and desktop shortcuts copied but my desktop layout, Firefox, etc all returned to default. I reformatted the partition and tried again, but with the same results. Even copying the data directly to the new from the old in the GUI didn't work to get me my old Firefox settings.

What's going on, what am I missing?  I thought that mounting the new partition as /home should just allow me to drop in my old /home settings. Any help would be appreciated.

Thanks, b

---

### Post by becominglumberg on 2007-04-09
How did you copy them? If you did a highlight & drag you may not have selected the many *many* hiden files that reside in /home.

---

### Post by bubzilla on 2007-04-09
I used the command given in the guide...

```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

I also tried directly copying the hidden files for Firefox from the .mozilla directory on the old /home to the new /home, which didn't appear to work.

---

### Post by bubzilla on 2007-04-09
OK, you were right, for some reason the hidden files didn't copy. Did it manually, and everything's fine!
Thanks, b

---


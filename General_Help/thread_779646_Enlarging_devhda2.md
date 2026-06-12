---
title: "Enlarging /dev/hda2"
date: 2008-05-02
forum: General Help
---

### Post by renegadeandy on 2008-05-02
Hi.

I an trying to do a system upgrade to 8.04LTS however when setting it up it says that i need an extra 320 mb ish on /

doing a df outputs the following:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              4846488   3787384    812908  83% /
varrun                  647340        96    647244   1% /var/run
varlock                 647340         0    647340   0% /var/lock
udev                    647340        84    647256   1% /dev
devshm                  647340         0    647340   0% /dev/shm
lrm                     647340     34696    612644   6% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             53689192  52317564   1371628  98% /windows
/dev/hda3              2901600    587720   2166484  22% /home


How can I enlarge the appropriate filesystem to accomodate the upgrade!

Thanks

Andy

---

### Post by renegadeandy on 2008-05-02
hello!!!! is there anyone who can help here?!

---

### Post by elmer_42 on 2008-05-02
I believe Gparted can do this. You should be able to shrink an unused section of a partition and then enlarge /dev/hda2. I'm almost positive that Gparted is in the repos, so just do this:
```
sudo apt-get install gparted
```

---

### Post by renegadeandy on 2008-05-02
I have gparted, and when right clicking on the partition in question it doesnt have a resize option becuase the partitions next to it are ntfs and hfs i think,

If you take alook at my df output - is there no commands I can follow to do this? I just need to freeup like 400 megs, but I dont have any work / games / apps to actually delete!

---


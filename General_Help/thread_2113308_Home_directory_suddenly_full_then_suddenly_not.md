---
title: "Home directory suddenly full then suddenly not"
date: 2013-02-07
forum: General Help
---

### Post by karn105 on 2013-02-07
This is the second time this has happened to me so I'd like to try and figure out what is going on.  Earlier today a message popped up saying that my home directory was full.  FIguring I needed to clean out some files I dove into my home folder and did a du -sh ~/* but nothing turned up that was over 1gb and my home directory is on a 150GB partition.

  I looked in the trash and for "." files that were large but nothing came up.  Not knowing what else to do, I restarted and now my home folder is 1GB where df was showing it  over 100gb before I rebooted.  I'd really like to get to the root of this problem since it's pretty annoying.

Thanks,
- Kevin

---

### Post by lisati on 2013-02-07
It could be that your /tmp folder was full, and that restarting cleaned it out.

---

### Post by karn105 on 2013-02-07
But isn't /tmp part of my root partition?  I have my hard drive partitioned thus
sda1 swap
sda2 /
sda3 /home

---

### Post by Impavidus on 2013-02-07
Could it be your .xsession-errors? Seems a common problem today.
[http://ubuntuforums.org/showthread.php?t=2113416](http://ubuntuforums.org/showthread.php?t=2113416)
[http://ubuntuforums.org/showthread.php?t=2112858](http://ubuntuforums.org/showthread.php?t=2112858)

---

### Post by karn105 on 2013-02-13
That indeed was it.  Thanks!

---


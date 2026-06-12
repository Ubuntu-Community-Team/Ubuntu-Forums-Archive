---
title: "/var full and size is different in partition manager and file explorer"
date: 2013-03-25
forum: General Help
---

### Post by Cranky_Frankie on 2013-03-25
I'm running 10.04. When I boot up I get a message saying /var is full. In the file manager it shows it at only 719meg, but it says "some contents can't be read." In Gparted it shows the partition at 42gig with 99% full.

I booted up with a boot disk and fsck'd /dev/sda6, which is /var. It says there are no problems. However Gparted still says it's full, I still get the boot up message that it's full, and the file manager still says it's only 719meb but "some contents can't be read." 

It appears there's a problem in /var that fsck can't fix. What do I do now?

---

### Post by Bashing-om on 2013-03-25
Cranky_Frankie; Hi !
A good probability is that the log files are filled up due to reporting (repeatedly) a system malfunction. To find large files on your system change directory to directories to be inspected and run terminal code:
```

cd /var/log
du -h --max-depth=1 | sort -hr
```
Isolate the fault, delete the old log files , and correct the fault.[INDENT=4]
hope this helps

[/INDENT]

---


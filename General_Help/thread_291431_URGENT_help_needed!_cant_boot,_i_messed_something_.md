---
title: "URGENT help needed! cant boot, i messed something up"
date: 2006-11-02
forum: General Help
---

### Post by trojanlinux on 2006-11-02
I really need to use my computer.  Last night i messed something up with the video settings and when I try to boot up I get a blue screen that says it cannot find  a monitor.  I can boot in recovery mode, though. Is there something I can type in to restore it to the way it was?  ALso please note I do not have a CD rom drive.  Help appreciated.

---

### Post by _simon_ on 2006-11-02
What exactly were you doing?

---

### Post by bigken on 2006-11-02
sudo dpkg-reconfigure xserver-xorg ;)

---

### Post by trojanlinux on 2006-11-02
ok thanks, but not i am running in 640 by 480, and i cant change it back. when i do the autodetect monitor the res still doesnt change.  is there a way to restore all defaults as if i were installing a fresh OS?

---

### Post by bulldog on 2006-11-02
If you made a backup before messing with xorg.conf,you can concider to put the backup in place of your messed up xorg.conf.

If not you have to figure out what you've changed and change it back.

---

### Post by bigken on 2006-11-02
you have use the space bar to select your resolution sizes and make you sure are using the correct video driver ;)

---

### Post by trojanlinux on 2006-11-02
> **bulldog said:**
> If you made a backup before messing with xorg.conf,you can concider to put the backup in place of your messed up xorg.conf.

If not you have to figure out what you've changed and change it back.

how do i do that?

---


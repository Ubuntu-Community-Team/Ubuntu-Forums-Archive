---
title: "General Hard Drive Help"
date: 2007-07-08
forum: General Help
---

### Post by philiaC on 2007-07-08
How do I get the ability to read/write important files on my main (FIlesystem) drive? And how do I automount and get the ability to read/write on my Storage drive (it is NTFS)?

---

### Post by bmorency on 2007-07-08
you want to open the terminal and type:

sudo aptitude install ntfs-3g
sudo ntfs-config

enable read/write support and it will make changes to your fstab and auto mount them the ntfs partitions.

---

### Post by philiaC on 2007-07-08
It says command not found when I try sudo ntfs-config.


EDIT: I still can't make either of them read/write.

---

### Post by bukwirm on 2007-07-08
You can use the sudo command (ie, sudo vim *filename*) or the gksudo command (for programs that have GUI's) to temporarily gain root powers, which should allow you to read/write those files. Be careful when using sudo - a mistake can really screw up your system.

---

### Post by philiaC on 2007-07-08
> **bukwirm said:**
> You can use the sudo command (ie, sudo vim *filename*) or the gksudo command (for programs that have GUI's) to temporarily gain root powers, which should allow you to read/write those files. Be careful when using sudo - a mistake can really screw up your system.

This really doesn't help at all. All I want is basic control over my hard drives, the ability to read/write whatever files I want...

---

### Post by philiaC on 2007-07-08
So, can anyone help?

---


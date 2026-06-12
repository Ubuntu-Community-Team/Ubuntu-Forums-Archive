---
title: "Slow performance on Celeron 650"
date: 2007-12-27
forum: General Help
---

### Post by grav on 2007-12-27
I've got an old Toshiba laptop with a Celeron 650 Mhz and 192 MB ram (max'ed out).

I've installed Ubuntu 7.10 using the minimal install cd and then a graphical front-end following [this guide]("http://www.psychocats.net/ubuntu/minimal").

I am a little surprised by the rather slow performance, seeing that the laptop ran WinME with IE 5 without many problems.

Is this to be expected, or is there something rotten about my linux installation?

---

### Post by dcstar on 2007-12-27
> **grav said:**
> I've got an old Toshiba laptop with a Celeron 650 Mhz and 192 MB ram (max'ed out).

I've installed Ubuntu 7.10 using the minimal install cd and then a graphical front-end following [this guide]("http://www.psychocats.net/ubuntu/minimal").

I am a little surprised by the rather slow performance, seeing that the laptop ran WinME with IE 5 without many problems.

Is this to be expected, or is there something rotten about my linux installation?

What kernel are you using?

---

### Post by grav on 2007-12-28
Assuming I'm doing the correct thing to check:

```

$ uname -r
2.6.22-14-generic

```

---

### Post by grav on 2007-12-30
I found [other threads]("http://ubuntuforums.org/showthread.php?t=586771&highlight=slow+kernel+toshiba") about similar problems, with both older Toshiba machines and the same kernel version.

So I tried installing Xubuntu 7.04 instead and doing an upgrade to 7.10, so now I can choose the kernel from 7.04 (2.6.20-15) in Grub, and the system is running smoothly.

---


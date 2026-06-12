---
title: "ubuntu 6.10 command-line and restricted-modules"
date: 2007-02-27
forum: General Help
---

### Post by szymon_g on 2007-02-27
hi.
i'm rather a beginner in linux/ubuntu.
i've installed on my laptop (acer asp 5680) a ubuntu 6.10 livecd, (almost) everything was great; but i would like to install on my laptop a command-line system and then to customise it (i mean: without gnome, without many unnecesery /in my opinion/ programs, i would like to add different windows and file manager etc), but i've got a 'small' problem: when i'm installing a command-line system from official 'alternate install' cd (or when i'm installing a polish version ubuntu 6.12 Elokwentny Emu PRO- it's basically a command-line system from alternate-cd of EE, but with standard polish manpages etc,), system cannot see my wireless card (intel ipw3945abg). the drivers for it are in linux-restricted-modules package.... so i have got (prabably silly) question: to install it, do i need only this package, or also a linux-headers etc? i'm asking becouse i do not heve a wired connection, i have to downloade this packages and save them on my windows' partition, and then mount part. and install them via dpkg -i.

thanks for any answer
szymon

---

### Post by caldevil on 2007-02-27
No, you don't need linux-headers

---

### Post by annda on 2007-02-27
hej Szymon!

writing in english since it's an english-language forum...

check out
packages.ubuntu.com
to see all the dependent packages you need. search for linux-restricted-modules and it will tell you everything you want to know!

---

### Post by szymon_g on 2007-02-27
thank you - coldevil & annda...
ps. annda- i'm learning english language :-)

---


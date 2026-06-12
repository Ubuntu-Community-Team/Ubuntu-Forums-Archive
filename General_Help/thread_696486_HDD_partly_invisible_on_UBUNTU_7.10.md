---
title: "HDD partly invisible on UBUNTU 7.10"
date: 2008-02-14
forum: General Help
---

### Post by SeniorII on 2008-02-14
Hello,

since updating from UBUNTU 7.04 (installed with WUBI 7.04.04) to 7.10 didn't work, I installed Ubuntu 7.10 with WUBI 7.10 alpha.

It works sufficiently, even my printer CANON PIXMA iP3000 had been recognized and doesn't need extra drivers compared with other LINUX versions.

I divided my hard disk (SATA, 250 GByte) into 3 logical drives: C:, D: and E: (NTFS).

WUBI and UBUNTU is installed on drive D: and reserves 10 GByte drive space.

Drive C: and E: are visible but not the exeeding part of drive D: that means that I cannot reach files on the WINDOWS part of drive D:.

On an earlier installation of UBUNTU 7.04 I didn't have that problem.

Has anybody an idea how to resolve the problem.

regards SeniorII

---

### Post by ago on 2008-02-14
The drive on which Wubi is installed should be accessible via /media/host in wubi 7.10, and /host in 8.04

Write access requires sudo

---

### Post by SeniorII on 2008-02-14
Hello ago,

BINGO

Thank you

regards SeniorII

---

### Post by gtype on 2008-02-14
hey there, same thing happens to me, i mean i can mount it and all, but ubuntu doesnt place it under my places or on desktop... any ideas why?

---

### Post by ago on 2008-02-14
The host drive is special. To make a long story short: it cannot be unmounted since it hosts your OS.

So yes it will not be treated as other devices.

---

### Post by gtype on 2008-02-14
thx for anwering, it is mounted on /host instead of /media/host. is this why it doesnt show on desktop? anyway to change it to /media/host? thx

---

### Post by ago on 2008-02-15
As mentioned, no, it will not go into media/host. Feel free to add a symlink or you can bindmount in /etc/fstab.

---

### Post by Totto90 on 2008-07-06
> **ago said:**
> The drive on which Wubi is installed should be accessible via /media/host in wubi 7.10, and /host in 8.04

Write access requires sudo

Hi I'm using 8.04, I'm totally new at this, where should I type or find /host

---

### Post by ago on 2008-07-06
In places, file system, /host

---


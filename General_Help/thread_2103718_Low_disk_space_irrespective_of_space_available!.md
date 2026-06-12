---
title: "Low disk space irrespective of space available!"
date: 2013-01-11
forum: General Help
---

### Post by vickykx68 on 2013-01-11
i installed ubuntu 10.10 inside windows..i have allocated a separate partion of 18gb.
but " /home" shows only 455MB of size and now i m out of space..pls help... :confused:

---

### Post by Wim Sturkenboom on 2013-01-11
Start a terminal in Ubuntu and post the output of
```

df -h

```
It will look similar to the below (command in red bold)
```

wim@webserver:~/backup$ **[COLOR="Red"]df -h[/COLOR]**
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p4      29G  3.6G   24G  14% /
/dev/cciss/c0d0p1     479M   27M  428M   6% /boot
/dev/cciss/c0d0p3     3.8G  135M  3.5G   4% /var
/dev/cciss/c0d1p1     270G   52G  205G  21% /home
wim@webserver:~/backup$

```

---

### Post by oldos2er on 2013-01-11
> **vickykx68 said:**
> i installed ubuntu 10.10 inside windows..i have allocated a separate partion of 18gb.


A Wubi install? Wubi installs Ubuntu into a special file inside your Windows partition. You could try [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) but it might be easier to backup any data you want to save, and reinstall Wubi with a 30GB file (the largest it can be). Or install Ubuntu onto its own partition(s).

---

### Post by vickykx68 on 2013-01-14
ya i agree,reinstall it..but is their a way so that i can increase size of \home directory which is just 455MB?

---

### Post by vickykx68 on 2013-01-14
> **Wim Sturkenboom said:**
> Start a terminal in Ubuntu and post the output of
```

df -h

```
It will look similar to the below (command in red bold)
```

wim@webserver:~/backup$ **[COLOR="Red"]df -h[/COLOR]**
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p4      29G  3.6G   24G  14% /
/dev/cciss/c0d0p1     479M   27M  428M   6% /boot
/dev/cciss/c0d0p3     3.8G  135M  3.5G   4% /var
/dev/cciss/c0d1p1     270G   52G  205G  21% /home
wim@webserver:~/backup$

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            4.6G  4.1G  308M  94% /
none                  1.9G  280K  1.9G   1% /dev
none                  1.9G  792K  1.9G   1% /dev/shm
none                  1.9G  244K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda9              13G  5.7G  7.0G  45% /host

---

### Post by 3rdalbum on 2013-01-14
> **vickykx68 said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            4.6G  4.1G  308M  94% /
none                  1.9G  280K  1.9G   1% /dev
none                  1.9G  792K  1.9G   1% /dev/shm
none                  1.9G  244K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda9              13G  5.7G  7.0G  45% /host

You allocated less than 5 gigs for Ubuntu, that's why you are out of space already.

Download the latest version of Ubuntu (12.10), or the latest long-term version (12.04). Ubuntu 10.10 is far too old now. Back up the data from the hard disk you have Ubuntu installed to now.Boot your computer from the Ubuntu 12.10 or 12.04 CD and follow the prompts to install Ubuntu to your 13 gigabyte hard disk.

This will give a better experience by far. Better yet, use a bigger hard disk.

---

### Post by vickykx68 on 2013-01-15
> **3rdalbum said:**
> You allocated less than 5 gigs for Ubuntu, that's why you are out of space already.

Download the latest version of Ubuntu (12.10), or the latest long-term version (12.04). Ubuntu 10.10 is far too old now. Back up the data from the hard disk you have Ubuntu installed to now.Boot your computer from the Ubuntu 12.10 or 12.04 CD and follow the prompts to install Ubuntu to your 13 gigabyte hard disk.

This will give a better experience by far. Better yet, use a bigger hard disk.
that simply great!!my space problem is solved but u know what...,the grub loader wont show me windows 7 boot option...i want both of them!!!

---


---
title: "Ubuntu server Ubuntu 16.04.4 LTS boot partition full"
date: 2019-01-22
forum: General Help
---

### Post by ckiikc on 2019-01-22
Hi, I have boot partition full on an Ubuntu server Ubuntu 16.04.4 LTS and I'm not able to update.
Could anyone help me please?
I'm not an expert.
My df command is:
```
df
Filesystem             1K-blocks     Used Available Use% Mounted on
udev                     1003992        0   1003992   0% /dev
tmpfs                     204836    25584    179252  13% /run
/dev/mapper/vg-lv_root  39711340 22522688  15464028  60% /
tmpfs                    1024160        4   1024156   1% /dev/shm
tmpfs                       5120        0      5120   0% /run/lock
tmpfs                    1024160        0   1024160   0% /sys/fs/cgroup
/dev/sda1                 472036   463106         0 100% /boot
tmpfs                     204836        0    204836   0% /run/user/0

```
My uname -r is:
```
uname -r
4.4.0-89-generic

```
My dpkg -l linux-image* linux-header* is
```
dpkg -l linux-image* linux-headers*
Voluto=U (non noto)/I (installato)/R (rimosso)/P (rimosso totale)/H (in attesa)
| Stato=Non/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(nessuno)/R (reinstallazione richiesta) (Stato,Err: maiuscolo=grave)
||/ Nome              Versione      Architettura  Descrizione
+++-=================-=============-=============-========================================
un  linux-headers     <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-3.0 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
ii  linux-headers-4.4 4.4.0-101.124 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-101.124 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-103.126 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-103.126 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-104.127 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-104.127 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-109.132 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-109.132 amd64         Linux kernel headers for version 4.4.0 o
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
ii  linux-headers-4.4 4.4.0-116.140 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-116.140 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-119.143 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-119.143 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-121.145 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-121.145 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-124.148 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-124.148 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-127.153 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-127.153 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-128.154 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-128.154 amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-141.167 all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-141.167 amd64         Linux kernel headers for version 4.4.0 o
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
ii  linux-headers-4.4 4.4.0-89.112  all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-89.112  amd64         Linux kernel headers for version 4.4.0 o
un  linux-headers-4.4 <nessuna>     <nessuna>     (nessuna descrizione disponibile)
ii  linux-headers-4.4 4.4.0-92.115  all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-92.115  amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-97.120  all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-97.120  amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-4.4 4.4.0-98.121  all           Header files related to Linux kernel ver
ii  linux-headers-4.4 4.4.0-98.121  amd64         Linux kernel headers for version 4.4.0 o
ii  linux-headers-gen 4.4.0.141.147 amd64         Generic Linux kernel headers
un  linux-image       <nessuna>     <nessuna>     (nessuna descrizione disponibile)
ii  linux-image-4.4.0 4.4.0-101.124 amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-103.126 amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-104.127 amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-109.132 amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-112.135 amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-116.140 amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-119.143 amd64         Linux kernel image for version 4.4.0 on 
iF  linux-image-4.4.0 4.4.0-121.145 amd64         Linux kernel image for version 4.4.0 on 
iF  linux-image-4.4.0 4.4.0-124.148 amd64         Linux kernel image for version 4.4.0 on 
iF  linux-image-4.4.0 4.4.0-127.153 amd64         Linux kernel image for version 4.4.0 on 
in  linux-image-4.4.0 <nessuna>     amd64         (nessuna descrizione disponibile)
in  linux-image-4.4.0 <nessuna>     amd64         (nessuna descrizione disponibile)
rc  linux-image-4.4.0 4.4.0-71.92   amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-78.99   amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-79.100  amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-81.104  amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-83.106  amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-87.110  amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-89.112  amd64         Linux kernel image for version 4.4.0 on 
rc  linux-image-4.4.0 4.4.0-91.114  amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-92.115  amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-97.120  amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-4.4.0 4.4.0-98.121  amd64         Linux kernel image for version 4.4.0 on 
ii  linux-image-extra 4.4.0-101.124 amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-103.126 amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-104.127 amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-109.132 amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-112.135 amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-116.140 amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-119.143 amd64         Linux kernel extra modules for version 4
iU  linux-image-extra 4.4.0-121.145 amd64         Linux kernel extra modules for version 4
iU  linux-image-extra 4.4.0-124.148 amd64         Linux kernel extra modules for version 4
iU  linux-image-extra 4.4.0-127.153 amd64         Linux kernel extra modules for version 4
iU  linux-image-extra 4.4.0-128.154 amd64         Linux kernel extra modules for version 4
iU  linux-image-extra 4.4.0-141.167 amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-71.92   amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-78.99   amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-79.100  amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-81.104  amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-83.106  amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-87.110  amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-89.112  amd64         Linux kernel extra modules for version 4
rc  linux-image-extra 4.4.0-91.114  amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-92.115  amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-97.120  amd64         Linux kernel extra modules for version 4
ii  linux-image-extra 4.4.0-98.121  amd64         Linux kernel extra modules for version 4
iU  linux-image-gener 4.4.0.141.147 amd64         Generic Linux kernel image

```

---

### Post by ajgreeny on 2019-01-22
It will help us more if you can run that **dpkg -l**  command again with a maximised terminal, as the output you show us has been truncated and we can not see the full kernel versions.

We need the full kernel version numbers in order to run a **dpkg -r** command now as it's most likely any **apt remove** command will fail due to insufficient headroom; the same will be so for the **apt autoremove** command which with recent Ubuntu versions should remove all but the two most recent kernel versions.

Once you have removed one or two kernels with **dpkg** the **sudo apt autoremove** command will probably work as it should and allow you to clean up the system properly.  You are then advised to run the autoremove command occasionally; I suggest doing so every time a new kernel is installed in your usual update process.

---


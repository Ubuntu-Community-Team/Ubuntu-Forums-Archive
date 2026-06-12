---
title: "grub error 17n recovery help!!"
date: 2008-06-05
forum: General Help
---

### Post by jnw222 on 2008-06-05
Help, i found while booting that rub just says 
loading strage 1.5
error 17

and nothing happens
how do i fix this 

Resorces on hand:
working windows xp on another computer with cd burner and internet acess
win xp install cd
win vista install cd
ubuntu 8.04 live cd
ubuntu 7.10 live cd


Dual boot config
dev/sda1 recovery partition (1.46 gigs ntfs)
dev sda2 Windows vista homebasic (51.29 gigs with boot ntfs)
dev/sda3 extended partition
dev/sda5 ubuntu 8.04 (20.58 gigs grub ex3
dev/sda6 swap (956.97 megs)
dev/sda7 ntfs (120 megs)
dev/sda8 fat32 (129 megs)

all partitions readable with hardy heron live cd

---

### Post by rraj.be on 2008-06-05
Grub  error 17  is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.
try  re installing grub.

To do that 


```
boot into your live cd.

open terminal
``` and type

```
sudo grub

find /boot/grub/stage1
```

if it returned like ```
hd(x,y)
```

type

```
root (x,y)

setup (x)

quit

sudo reboot
```

Now it should be solved.

May i know if this does'nt worked.

---

### Post by jnw222 on 2008-06-05
grub menu boots up (using hidden menu)
vista works fine but ubuntu returned

returned at startup
> grub error 17 
can not mount selected partiton


i will upload menu.lst later

---

### Post by rraj.be on 2008-06-05
Just try super GRUB.
IT should help you.

You can get it here

```
[www.geocities.com/supergrubdisk/]("www.geocities.com/supergrubdisk/")
```

---

### Post by jnw222 on 2008-06-05
here is menu.list

[http://jnw222.parahosting.net/test/menu.lst]("http://jnw222.parahosting.net/test/menu.lst")

---


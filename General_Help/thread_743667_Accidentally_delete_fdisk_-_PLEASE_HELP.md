---
title: "Accidentally delete fdisk - PLEASE HELP"
date: 2008-04-02
forum: General Help
---

### Post by kingleer on 2008-04-02
I accidentally deleted fdisk. 

Every time I try writing 

> 
sudo fdisk -l
 

In the terminal, I get

> 
sudo: fdisk: command not found
 

Going into root (su -) gives the same result. 

WHAT APPLICATION DO I HAVE TO INSTALL TO GET FDISK back?

---

### Post by fragos on 2008-04-02
I did find a package gnu-fdisk which claims to be fdsk+. If you're running firefox there is an Ubuntu search engine that you can ask that question of. I'm an Epiphany user.

---

### Post by kingleer on 2008-04-02
I installed gnu-fdisk, but now i get 

> 
kinglear@kinglear:~$ sudo fdisk -l

Disk /dev/sda: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
Segmentation fault (core dumped)


---

### Post by ibuclaw on 2008-04-02
type in:
```
 locate fdisk 
```

Just to be sure it isn't hidden somewhere...

Here's my printed output:
```

/sbin/cfdisk
/sbin/fdisk
/sbin/sfdisk
/usr/share/doc/util-linux/README.cfdisk
/usr/share/doc/util-linux/README.fdisk.gz
/usr/share/doc/util-linux/examples/sfdisk.examples.gz
/usr/share/man/man8/cfdisk.8.gz
/usr/share/man/man8/fdisk.8.gz
/usr/share/man/man8/sfdisk.8.gz

```
Perhaps you could use **sfdisk** or **cfdisk** to meet your needs. 

I recommend "cfdisk"
Its a lovely curses view, and you can have a clear idea of what you are doing!

Regards
Iain

---

### Post by kingleer on 2008-04-02
locate fdisk gives me

> 
/usr/share/man/man8/fdisk.8.gz
/usr/share/man/man8/cfdisk.8.gz
/sbin/fdisk
/sbin/cfdisk
 

cfdisk works for me, but it still bugs me that fdisk is gone.

---

### Post by ibuclaw on 2008-04-02
Had a small look round, you can try reinstalling every package in ubuntu minimal again... Though that, I think would be risky.

[Here's a link to the ubuntu packages site that lists them.]("http://packages.ubuntu.com/gutsy/ubuntu-minimal")

I presume that it would be hidden somewhere in one of them.

Else, you could just wait 2 weeks for Hardy to come out and install a fresh new system

Regards
Iain

---

### Post by ryanhaigh on 2008-04-02
fdisk is provided in the packages util-linux and busybox, reinstall those and you shoud be good to go (don't know which is actually installed by default but I would guess util-linux as busybox is in universe although anyone who has had grub issues will probably tell you otherwise including me)
```
sudo apt-get install --reinstall util-linux
```

---

### Post by kingleer on 2008-04-02
> 
fdisk is provided in the packages util-linux and busybox, reinstall those and you shoud be good to go (don't know which is actually installed by default but I would guess util-linux as busybox is in universe although anyone who has had grub issues will probably tell you otherwise including me)


Thanks, I found a solution by installing the following deb.

[http://packages.debian.org/sarge/fdisk-udeb](http://packages.debian.org/sarge/fdisk-udeb)

but thanks everyone for all your help. I really appreciated it.

---


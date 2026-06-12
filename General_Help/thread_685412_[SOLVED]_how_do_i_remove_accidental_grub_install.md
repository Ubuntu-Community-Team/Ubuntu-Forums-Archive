---
title: "[SOLVED] how do i remove accidental grub install?"
date: 2008-02-02
forum: General Help
---

### Post by tuwe on 2008-02-02
Hi,

I run Ubuntu 8.04 / OSX Dualboot on a Macbook Pro.
i just tried to install grub-gfx (following a howto from wiki.ubuntuusers.de), and while perfoming grub-install, i accidentally typed /dev/sda3 instead of /dev/sda (although i am not sure if that's where i wanted to install grub to?), and ended up with 2 linux installations showing up in the rEFIt boot menu. Both of them work fine, but it is quite annoying to have two options to choose from.

So, my questions are:
How do I remove grub from /dev/sda3? 
How do I find out where to install grub?

Most threads I found here were about uninstalling ubuntu and run fixmbr or something, but thats clearly not what I want to do.
The grub faq states that there is no uninstall option though, only the possibility to overwrite grub. 

Here's the output of sudo fdisk -l:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Platte /dev/sda: 120.0 GByte, 120034123776 Byte
255 Köpfe, 63 Sektoren/Spuren, 14593 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        2630    20919148   af  Unbekannt
/dev/sda3   *        2630       14224    93125977   83  Linux
/dev/sda4           14224       14594     2970862+  82  Linux Swap / Solaris

```

thanks for any help.

---

### Post by dcstar on 2008-02-03
> **tuwe said:**
> Hi,

I run Ubuntu 8.04 / OSX Dualboot on a Macbook Pro.
i just tried to install grub-gfx (following a howto from wiki.ubuntuusers.de), and while perfoming grub-install, i accidentally typed /dev/sda3 instead of /dev/sda (although i am not sure if that's where i wanted to install grub to?), and ended up with 2 linux installations showing up in the rEFIt boot menu. Both of them work fine, but it is quite annoying to have two options to choose from.
..........

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by tuwe on 2008-02-04
Thanks for your suggestion, but...

I prefer vi. :)
I am perfectly happy with my menu.lst. I do not want to remove duplicate menu entries, I want to remove a duplicate grub installation. I'm sorry if I wasn't clear enough in my previous post.
With the help of [this script]("http://wiki.ubuntuusers.de/Baustelle/Skripte_GRUB_finden"), I was able to obtain the following output:
```
----------------------------------
/dev/sda	GRUB found
/dev/sda1	No GRUB found
/dev/sda2	No GRUB found
/dev/sda3	GRUB found
/dev/sda4	No GRUB found
----------------------------------
```

So, how do I remove grub from /dev/sda3 ?

---

### Post by HHelsinger on 2008-02-15
I have the same problem, having accidentally written GRUB to /dev/sda rather than /dev/sdb.   

I saw a suggestion somewhere that running fdisk /mbr in DOS might clean it up, but I am wary of that without confirmation.   

I suppose the earlier suggestion in this thread, to edit /boot/grub/menu.lst would serve, if you comment out all of the menu choices but the one you want (Windows?), and change the delay to 0.    It would be cleaner, however,  to remove GRUB entirely from the partition where it doesn't belong.

---

### Post by miqie on 2008-02-15
The Super Grub disk  ( [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) ) has an option to remove grub from your harddrives.

---

### Post by adrian15 on 2008-02-18
> **tuwe said:**
> Hi,

I run Ubuntu 8.04 / OSX Dualboot on a Macbook Pro.
i just tried to install grub-gfx (following a howto from wiki.ubuntuusers.de), and while perfoming grub-install, i accidentally typed /dev/sda3 instead of /dev/sda (although i am not sure if that's where i wanted to install grub to?), and ended up with 2 linux installations showing up in the rEFIt boot menu. Both of them work fine, but it is quite annoying to have two options to choose from.

So, my questions are:
How do I remove grub from /dev/sda3? 

Remove partition boot loader from an ext3 partition: (Do not do this on a reiserfs partition).

```

dd if=/dev/zero of=/dev/sda3 count=1 bs=512

```

adrian15

---


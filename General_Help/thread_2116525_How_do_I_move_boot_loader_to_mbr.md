---
title: "How do I move boot loader to mbr ?"
date: 2013-02-16
forum: General Help
---

### Post by Acaster on 2013-02-16
So I installed 11.10 to the first partition of the second disk with the idea that I would eventually swap the disks around and use 11.10 while I got the other disk sorted but I put the boot loader on / during installation when I should have put it on /dev/sdb.
 Had a good surf around the subject and there's a lot of complicated stuff out there and not a lot of material here under the keywords Move Grub to Mbr and the textbook is expensive but can somebody please tell me if I got the right answer before I take the plunge ? It could save me another installation.

 Is it as simple as booting 11.10 and entering grub-install /dev/sdb  in a terminal?

---

### Post by carl4926 on 2013-02-16
You should put grub on sda

```
sudo grub-install /dev/sda
```

---

### Post by fdrake on 2013-02-16
> **Acaster said:**
> So I installed 11.10 to the first partition of the second disk with the idea that I would eventually swap the disks around and use 11.10 while I got the other disk sorted but I put the boot loader on / during installation when I should have put it on /dev/sdb.
 Had a good surf around the subject and there's a lot of complicated stuff out there and not a lot of material here under the keywords Move Grub to Mbr and the textbook is expensive but can somebody please tell me if I got the right answer before I take the plunge ? It could save me another installation.

 Is it as simple as booting 11.10 and entering grub-install /dev/sdb  in a terminal?

simply reainstall the bootloader, use a live cd for it:
[http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

---

### Post by oldfred on 2013-02-16
If you have an old IDE system you may have to install to sda.

But most new systems let you boot from either sda or sdb from BIOS settings, so you can install grub to sdb as you originally posted.

If BIOS lets you I prefer to have grub2's boot loader in the MBR of the same drive as the install. Then when other drive fails you can still boot. Corollary is to have an operating system on every drive, so even if one drive fails I can boot another.

---

### Post by dcstar on 2013-02-17
> **Acaster said:**
> 
.........
 Is it as simple as booting 11.10 and entering grub-install /dev/sdb  in a terminal?

```
sudo dpkg-reconfigure grub-pc
```

---


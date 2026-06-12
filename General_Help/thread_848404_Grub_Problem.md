---
title: "Grub Problem"
date: 2008-07-03
forum: General Help
---

### Post by saikot on 2008-07-03
hi 
good XXX[morning/noon/afternoon].im having a problem with my fedora installation.i edited my menu.lst and now pulling my hairs out.i have windows xp(sp2) & fedora installed on a single hard drive.while editing i commented out the title fedora from the menu.lst file as a result my fedora option is deleted from the grub list.so i cnt get access to my fedora anymore.so if anyone can hav anything to offer plz reply.

note:i tried on reinstalling the grub but it didn't help.

---

### Post by Titan8990 on 2008-07-03
On Fedora the file you are looking for is grub.conf. Ubuntu is the only distro I know of that uses the menu.lst file.

---

### Post by VMC on 2008-07-03
> **Titan8990 said:**
> On Fedora the file you are looking for is grub.conf. Ubuntu is the only distro I know of that uses the menu.lst file.

This is not true. If you read the Grub 097, menu.lst is part of the system. Maybe Fedora uses Grub2, I don't know.

The OP did mentioned that after he commented Fodora out , it quite working.

I did notice that when I installed the latest Fedora, it had a special /boot partition. I have since removed Fedora.

I would just boot using a livecd and do the :

```
sudo grub
find /boot/grub/stage1
```

Or if you know where it is edit "/boot/grub/menu.lst"

if using ubuntu livecd type:

```
sudo fdisk -l
```

that might be of helo for us.

---

### Post by Titan8990 on 2008-07-03
I have used both Fedora Core 5 and 8. In both occassions I edited grub.conf. I did see that menu.lst was there but my RHEL book specifically says to edit grub.conf. I believe that Fedora uses it's own version of GRUB as its GRUB is a graphical menu that says "Fedora" on it...

> I did notice that when I installed the latest Fedora, it had a special /boot partition. I have since removed Fedora.

This is "recommended" for RHEL. I always set up my partitions manually and I suggest that other people do the same.

I also found that the version of Slakware I use uses grub.conf.

---

### Post by ajgreeny on 2008-07-03
In fedora the menu.lst file is a link to grub.conf, so in theory it has both files; grub.conf is the text file however and that is what needs editing.
Run a live CD such as ubuntu, mount the partition where fedora's /boot/grub folders are (I think sometimes fedora puts them on a separate boot partition), open the grub.conf file as root with ```
gksudo gedit /path/to grub.conf
``` and remove the comment mark from the list.  Simple as pie!

Other live CDs may need a different command to open the file as root, but I think all will allow it somehow.  If you dont have a live CD download puppy linux and burn that and run it.  That distro runs as single user (root) by default, I think, so will enable you to edit the file easily.

---


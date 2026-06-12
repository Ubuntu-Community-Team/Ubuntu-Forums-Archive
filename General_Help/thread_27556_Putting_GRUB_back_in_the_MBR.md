---
title: "Putting GRUB back in the MBR"
date: 2005-04-16
forum: General Help
---

### Post by Giturar on 2005-04-16
Just recently I had to reinstall windows (for games, thats it), and now I lost GRUB, which is probably becuase windows wrote its own MBR. How do I get the grub mbr back? Thanks.

Also, I dont have a floppy drive in this computer.

---

### Post by nad on 2005-04-16
Ahhh... the reason to have a rescue disk. Since you can't use a floppy, how about an ubuntu live cd. You then mount your linux file system, issue the chroot command to its' root and run update-grub.

Otherwise download and burn a copy of UBCD (ultimate boot cd). Dozens of tools including linux boot images. RTFMs and issue your chroot with grub | grub-install | update-grub depending upon your resources.

Dan M

---

### Post by Giturar on 2005-04-16
Alright, so I would mount the root partition, but since grub is in the /boot partition, do i mount that too?

---

### Post by nad on 2005-04-16
If /boot is a separate filesystem, yes. You will then have to pass the location to install grub on the command line.

Dan M

---


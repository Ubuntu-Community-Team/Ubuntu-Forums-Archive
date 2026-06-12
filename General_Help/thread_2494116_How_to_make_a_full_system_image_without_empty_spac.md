---
title: "How to make a full system image without empty space?"
date: 2024-01-05
forum: General Help
---

### Post by norvel4 on 2024-01-05
How do I use **Disks** to make a system image with full restore possible and only storing filled space on like my Ubuntu 22.04.3 LTS with Ubuntu Pro Lenovo Thinkpad T460? I tried making a partition image of like my Ubuntu partition but it tries to make a full with all empty space included partition image and that partition is 2TB so that is impractical. I am trying for a full backup that I can restore all things that were on original using. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by Holger_Gehrke on 2024-01-05
Full disk images are not meant as a normal backup. They are mostly used on breaking or broken disks as part of an attempt to recover what data one can. In this cases the copying of blocks the potentially broken file system claims are unused is actually needed. They are also of some use in doing mass-deployment on identical machines - install one machine then image it and make as many copies as you have machines.

A real backup should give the user the option of selectively restoring single files or groups of files. In the best case it should also be possible to go back multiple generations of one or more files. All of that is not possible or not practical with images. With Ubuntu the installation is so quick and easy that wiping, reinstalling from scratch, reinstalling the programs you installed (command line install from a list you keep updated when you install something; there are ways to generate such a list from the package manager but you have to do that before a system is broken to the point that you need it ...) and restoring a backup only of changed system configurations and user data is usually quicker than using an imager.

One imager that understands the common filesystems on Linux well enough to only store used blocks is [clonezilla]("https://clonezilla.org/").

Holger

---

### Post by norvel4 on 2024-01-05
I just would like a full system thing so I can restore everything on this computer and have it only store filled space so can this be done or am I stuck with rsync?

---

### Post by HermanAB on 2024-01-06
Look at fsarchiver.

---

### Post by The Cog on 2024-01-06
I have used fsarchiver to save and restore a full system before now. It worked as expected.
But there are 2 things you need to do in addition after restoring the system partition (if I remember correctly):
- reinstall the bootloader. This can be done from a live CD by chroot to the restored partition and running grub-install
- edit /etc/fstab and correct the UUID.

Edit: That was before GPT came about. It may be more complicated these days.

---


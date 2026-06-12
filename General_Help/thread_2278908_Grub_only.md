---
title: "Grub only"
date: 2015-05-19
forum: General Help
---

### Post by Raures on 2015-05-19
Hi, I am a windows-only user. I bought this laptop which has Ubuntu on it, in my tryings of uninstalling this thing I got stuck at something. I've got a Win7 cd and I tried to make Ubuntu boot from it in bios (Toshiba Utility Setup, or something), it didn't work. Then I tried this software, Grub Customizer, I removed all the configurations from the first tab, so my laptop could only boot from cd (at least that's what I thought), it also didn't work. Now all I have is Gnu Grub, Toshiba Utility Setup and my Win7 cd. Help?

---

### Post by Vladlenin5000 on 2015-05-19
Hi and welcome.

Operating systems don't need to be "uninstalled". 

What you're trying to do is to install Windows 7. In order to do that all you need is its installation media. Boot from it and follow instructions. At some point you'll be asked where to install. In the same windows there are a few buttons for managing partitions -> You want to delete ALL existing partitions. You may need to create a new one (NTFS) or the Windows may pick up from there and automatically partition the now unallocated space. Proceed with the installation. DONE.

This has nothing to do with Ubuntu. If you need help installing Windows I suggest you ask in Windows forums.

---

### Post by Raures on 2015-05-20
I do not know how to boot from 'media'. Because Ubuntu doesn't let me.

---

### Post by Vladlenin5000 on 2015-05-20
No, nothing to do with Ubuntu.

There's probably a one time boot key to select CD/DVD and also the boot order priority in BIOS/UEFI. That's something hardware related and varies from manufacturer from manufacturer. READ YOUR MANUAL. If you don't have it now you can probably find it online. And you NEED to know all your hardware specifications: Unlike Ubuntu or any major Linux distro which have native - built in the kernel - support for lots of hardware, Windows most likely will require lots of drivers after the main OS installation therefore you need to know exactly what to look for  

However, my advice is to seek professional help.

---

### Post by Raures on 2015-05-20
I fixed it. Switching booting mode from UEFI to CSM made my laptop boot from CD/DVD, which allowed me to install the OS, but not before 'cleaning' the disk, to get rid of gpt. Everything is working as for now, thank you for your reply.

---

### Post by Vladlenin5000 on 2015-05-20
You're welcome. :p

Enjoy your viruses, malware and backdoors. :lolflag:

---


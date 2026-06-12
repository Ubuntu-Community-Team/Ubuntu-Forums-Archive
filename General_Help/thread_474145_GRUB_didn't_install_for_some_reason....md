---
title: "GRUB didn't install for some reason..."
date: 2007-06-14
forum: General Help
---

### Post by ByKeLaO on 2007-06-14
I have 2 hard disks:
- 320GB with the v word (Home Premium) installed
- 80GB with Ubuntu installed (I think)

I installed Ubuntu on my 80GB hard disk, rebooted, and the boot process skipped straight to vista with no GRUB loader. I tried booting directly to my Ubuntu disk and it told me the media was invalid and asked me to restart. So now I have a disk with Vista on it, and a disk with Ubuntu on it, but with no means to boot into Ubuntu!

So, how do I install GRUB (or some other bootloader) on my computer? And also, why didn't Ubuntu install it for me?

---

### Post by logos34 on 2007-06-14
This [link]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") might shed some light on your error message.  

You can try reinstalling grub from the live cd, but to avoid confusion and accidentally overwriting your vista bootloader on the 320gb drive (which may be '(hd0)' or '(h1)'), I'd put it on a floppy first and test it:

edit:
just use this 
[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29%7C%28grub%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29%7C%28grub%29)

If you don't have a floppy drive, download [SuperGrub]("http://supergrub.forjamari.linex.org/")

---

### Post by ByKeLaO on 2007-06-15
Thanks for your fast reply!

I've made a bootable super GRUB disk. I booted into it and tried installing GRUB as my MBR on my second disk (I'm scared about breaking my Vista installation, because I'm installing Ubuntu over my backup ;)). I then tried booting the disk and it still didn't work.

So I tried directly booting Ubuntu from the super GRUB disk. It recognized the disk and its partitions, but I couldn't get it to boot! Something about the executable being in the wrong format (I forget the exact error message). So I tried booting Vista using the GRUB disk and it worked fine.

So I guessed this was a problem with my Linux installation. I reinstalled, using the entirety of the 80GB disk, and tried again, with no success!

What's wrong with Linux? Why won't it work on my PC?!?

---

### Post by ByKeLaO on 2007-06-15
BTW, I only want Linux so I can dabble with compiling my own distro. As I understand it, Linux cannot be compiled under Windows, so I need a copy of Linix. If Ubuntu doesn't work, I shall be forced to use some other distro :(

---

### Post by ByKeLaO on 2007-06-15
I'm gonna try using EasyBCD. If that doesn't work I'll have to restore my MBR and forget about Linux for now...

Wish me luck! :D

---

### Post by ByKeLaO on 2007-06-20
No, it's no use... It would appear that my Ubuntu installation is unbootable.
Perhaps my IDE disk is set as a slave? It's hard to tell because my cable does not have master/slave configuration. I have a splitter into which both my IDE hard disk and DVD drive are both connected. Maybe this setup doesn't allow for a bootable disk? I assume it does though, since my BIOS recognizes the IDE disk as a master...
Any suggestions, anyone?

---


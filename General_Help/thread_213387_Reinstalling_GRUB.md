---
title: "Reinstalling GRUB"
date: 2006-07-11
forum: General Help
---

### Post by Mishal on 2006-07-11
Recently I have gone nuts and now I have 4 OS: 3 Linux and 1 Windows.:) 

Windows: Installed for a long time and have recently become corrupt when i deleted Breezy and installed Dapper though I don't know why. Now I want to reinstall it.

Ubuntu Dapper: Installed in early June and GRUB was installed to overwrite MBR of Windows.

MEPIS: this installed another GRUB on top of that of Ubuntu. So now I am stuck with MEPIS' grub.

Ubuntu Edgy: thought I would give it a try and have installed Dapper and then apt-get dist-upgrade.

Anyway, now I am stuck with MEPIS' grub which I don't like very much and also I am going to reinstall Windows which (I have heard) likes being the only installation in a system.

So, I have two questions:

1) If I simply reinstall Windows now, will my MEPIS grub disappear because Windows will try to write on the MBR again?

2) How do I bring back my Ubuntu GRUB and be able to boot to all 4 OS nicely?

:) :)

---

### Post by Rui Pais on 2006-07-11
> **Mishal said:**
> Recently I have gone nuts and now I have 4 OS: 3 Linux and 1 Windows.:) 

(...)


1) If I simply reinstall Windows now, will my MEPIS grub disappear because Windows will try to write on the MBR again?

2) How do I bring back my Ubuntu GRUB and be able to boot to all 4 OS nicely?

If i understand right you didn't delete neither Ubuntu nor Windows?

If that was the case, just edit your (mepis) grub/menu.lst and add:

> 
title	Ubuntu Dapper, kernel 2.6.15-25-686 
	root		(hd1,0)
	kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hdb2 ro quiet splash=silent resume=/dev/hda7 vga=792
	initrd		/boot/initrd.img-2.6.15-25-686
	savedefault
	boot

title Windows
	rootnoverify (hd0,0)
	chainloader +1


replacing of course your partition numbers and kernel versions. You can mount your ubuntu partitions on mepis to check installed kernel versions.


Any doubts, check the [Grub's Wiki page]("https://help.ubuntu.com/community/GrubHowto").


Edit: here it is the [Howto for reintall Grub after Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---


---
title: "Installing ubuntu I get grub installation failed"
date: 2018-08-19
forum: General Help
---

### Post by tackskull on 2018-08-19
Hello everyone :)

My pc is a laptop lenovo ideapad 320:

 processor: AMD A10-9620P
Ram: 8Gb
video card: AMD Radeon R7
Hard disk: 1Tb

Before I was using Ubuntu 18.04 but the system was unstable gaving me many freeze and programs crashes (the system was installed on just one partition and a swap partition made after the installation). So i decided to format it with gparted making three partitions: 20gb for root / - 16gb for swap - the rest for /home.

The problem is that when I launch the installation of my new ubuntu (in this case Ubuntu Mate 64 bit) everything seems to go ok but near to the finish an error message apper telling me "The 'grub-pc' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot".

I tryed with different ubuntu distro like Ubuntu Mate and Kubuntu but the problem is the same. So I try to do a normal installation of ubuntu mate erasing the entire hard disk without partitioning and everything go ok, but after using a bit I have noticed that the sstem is again unstable getting programs crash.

So without know nothing about pc and programming I think I have a problem with my hard disk that is  ruined in some ways. I remember with my first ubuntu installation the system started to be unstable after the massive download of torrent files via transimmion and the massive unzip of archive files. Maybe I have ruined the internal hard disk with so many files? About 700gb.

So can you guys help me to figure what is my problem installing any kind of ubuntu and why in the case of a normal installation any kind of ubuntu system I install is unstable?

Thanks everybody

---

### Post by oldfred on 2018-08-19
Since newer PC, it is UEFI with gpt partitioning.
Preferable to install in UEFI boot mode, but you should be able to install in the now 35 year old BIOS boot mode.

But drive was gpt as the standard for use with UEFI. To install in UEFI mode, then you must have an ESP - efi system partition FAT32 100 to 500MB with boot flag.
If installing in old BIOS boot mode to a gpt drive, you have to have the bios_grub partition which is 1 or 2MB unformatted with bios_grub flag.

Your error on grub not installing is saying you did not have the correct supporting partition. If grub-pc error it then was a BIOS type install and no bios_grub.

How you boot install media UEFI or BIOS is then how it installs. You may need various settings in UEFI to allow install.

You should also update UEFI from Lenovo for your system, but that resets many of the UEFI settings. I keep a list as I change 5 or 10 settings some required and some optional.

---


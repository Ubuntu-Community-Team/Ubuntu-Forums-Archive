---
title: "GRUB 2, incorrect entry for ArchLinux"
date: 2013-06-12
forum: General Help
---

### Post by gigenieks on 2013-06-12
Hello!

I have installed (by "installed" I mean I did all the [installation steps]("https://wiki.archlinux.org/index.php/Beginners'_Guide#Installation"), none of Post-installation) ArchLinux on /dev/sda2.
I _did not_ reinstall Ubuntu's GRUB2, when I was done installing Arch, I started Ubuntu and did
```
sudo update-grub
```
which added menuentry for Arch.

When I tried to boot Arch I got this:
[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/ArchLinux/th_IMAG0430_zpse9fe1f6d.jpg[/IMG]](http://s59.photobucket.com/user/gigenieks/media/ArchLinux/IMAG0430_zpse9fe1f6d.jpg.html)

[Here]("https://bbs.archlinux.org/viewtopic.php?id=165047") is my thread in ArchLinux forums.
I'll quote one of posts:
> 
..but the problem is in the boot loader configuration.  Grub tries to automate many things for you, but with that automation comes some assumptions - it doesn't always make the right assumptions.  It seems to have assumed your root partition is dev/sda2, is this correct?  It has also detected that partition as ntfs, is this correct?

Yes, my Arch'es root partition is on /dev/sda2. No, partition is ext4.

Another member posts:
> 
There is one potential issue that you should know about, however:
Some people who do this, at some time, have found that the OS-Prober doesn't find the Arch installation.

The way to fix/prevent it is simple:
In Ubuntu, find your /etc/lsb-release file.  Make a version of that in your Arch /etc/ folder (edited appropriately).  That is something that helps the OS-Prober "find" another linux.  If it finds that file, it will see the linux install.

The keywords are **edited appropriately**. Anyone can help?

I'm kinda lost...

---

### Post by oldfred on 2013-06-12
If you did not install Arch's grub somewhere then it did not create its own grub menu file. Ubuntu's os-prober uses that file to create its own entry for Arch. If not found then it tries a basic boot of some sort. You may need to manually enter a grub boot stanza into 40_custom.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
just change ghe values to what is correct for Arch, I.e.
```
DISTRIB_ID=Arch
DISTRIB_RELEASE=2013.06.01
DISTRIB_CODENAME=Arch
DISTRIB_DESCRIPTION="Arch Linux"
```

---

### Post by gigenieks on 2013-06-13
> **oldfred said:**
> 
Post the link to the BootInfo report that this creates.

[http://paste.ubuntu.com/5760505/](http://paste.ubuntu.com/5760505/)

Note: After installing Boot-Repair it run automatically and asked me
> 
Is sda (120B) a removable disk?

It isn't. Why it asked me this??

---

### Post by fantab on 2013-06-13
If you have Ubuntu 12.04 then you have to mount the Arch partition before you run 'update-grub'.

---

### Post by gigenieks on 2013-06-13
I'm using Ubuntu 13.04

---

### Post by fantab on 2013-06-13
Then you may have to reinstall ARCH. I also boot Arch and I have not installed GRUB from ARCH. I have no problems booting Arch from Ubuntu-Grub.

Your BootInfo summary looks alright to me.

---

### Post by oldfred on 2013-06-13
Are files in /boot or up one level. Example here is slightly different, but I do not boot Arch.

[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

> 
# (0) Arch Linux menuentry "Arch Linux" { 
  set root=(hd0,1) 
  linux /vmlinuz-linux root=/dev/sda3 ro 
  initrd /initramfs-linux.img 
} 


---


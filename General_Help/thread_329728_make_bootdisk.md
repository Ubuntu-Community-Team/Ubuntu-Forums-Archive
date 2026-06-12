---
title: "make bootdisk?"
date: 2007-01-02
forum: General Help
---

### Post by Stochastic on 2007-01-02
Hi I'm in the process of attempting to get Stanton Magnetics' Final Scratch version1.0 software runnin on my Ubuntu Dapper compy and am wondering if there's an easy way to restore a broken grub (possibly by way of bootdisk)? It's not broken now but it will be as soon as I attempt to install Final Scratch again.
Here's the deal:
     The software is an audio application that is housed within a Debian-based distro.  It's written to install itself into a folder on a fat32 partition and replace windows bootloader with grub, leaving an option to boot off that partition (windows - or so it assumes, my fat32 is merely a data partition).  I attempted a regular install to see if it would autodetect that I have a linux distro on a different partition but no such luck so I was forced to uninstall the software and reinstall Ubuntu.  I believe the grub version final scratch uses is 0.9 but I'm not 100%
     Basically I'm thinking that it would be best to somehow run the final scratch software through Ubuntu rather than having to boot into an entirely new os for one app.  Is this possible?  Maybe even as a virtual machine?  Or can anyone give me advice on how I might alter grub.conf files to get the two systems to work together?

---

### Post by jblebrun on 2007-01-02
You could just boot with the Ubuntu live CD, which will give you the capability to modify your drive in any way you want. 

You don't need to re-install any OSes. Just figure out which partition is your boot partition, and edit /boot/grub/menu.lst in that partition. Check out what the boot parameters for your current Ubuntu installation look like in /boot/grub/menu.lst... just copy those to the new grub/menu.list that gets created.

---

### Post by Stochastic on 2007-01-02
Final scratch turns my fat32 partition into the boot partition and uses an earlier version of grub.  Will the grub versions make it difficult to backport ubuntu into it?  I'd like to keep the later grub version and just edit that to accomodate final scratch, is that possible through the live cd?  Actually what I'd really like to do is get final scratch running  within ubuntu, can anyone give me a hand with that?

---

### Post by jblebrun on 2007-01-02
> **Stochastic said:**
> Final scratch turns my fat32 partition into the boot partition and uses an earlier version of grub.  Will the grub versions make it difficult to backport ubuntu into it?  I'd like to keep the later grub version and just edit that to accomodate final scratch, is that possible through the live cd?  Actually what I'd really like to do is get final scratch running  within ubuntu, can anyone give me a hand with that?

Errr, why can't you install FS and then Ubuntu? Anyway, try this:

1. Install Ubuntu.
2. Install FS.
3. Boot from the Ubuntu Live CD. 
4. Figure out which *drive* and which *partition* has your ubuntu's /boot/grub directory.
5. open a terminal window.
6. Run grub (just type *grub*)
7. Within grub, type *root (hd#,#)* (see more below about what the # should be)
8. Finally, type *setup (hd#)*

Here's how linux drives and partitions translate into grub drives:
/dev/hda = hd0
/dev/hda1 = hd(0,0)
/dev/hda2 = hd(0,1)
/dev/hdb = hd1
/dev/hdb1 = hd(1,0)
/dev/hdb2 = hd(1,1)
etc.

Grub should now be fixed to the original Ubuntu version. Now, just copy the entry from FS's boot/grub/menu.list into your ubuntu's boot/grub/menu.list, and it should work. You may have to tweak a few things here or there.

---

### Post by Stochastic on 2007-01-02
Okay, now I've got both systems running but I'm already getting tired of rebooting to go between systems.  Any hints on fixing that?

---

### Post by jblebrun on 2007-01-02
Probably the reason it installs its own Linux environment is that it is (I assume) a real-time audio application. The standard Linux kernel isn't so good for real-time audio. Boot into Final Scratch, go to a terminal, and find the output of **uname -r** to see the kernel version... it may indicate that some patches are installed. 

If it *doesn't* need a special environment, try just mounting the partition that it's on, and running it...

---


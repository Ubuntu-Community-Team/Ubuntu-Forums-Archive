---
title: "How to move my current install to a new computer?"
date: 2018-07-17
forum: General Help
---

### Post by lsutiger on 2018-07-17
I have an install that I want to move to my new computer. I used to just swap the hard drives, but this is an UEFI install. The new computer does not see the OS. How can I accomplish this without having to do a reinstall?

---

### Post by TheFu on 2018-07-17
You can't, at least not easily.   But for a typical desktop, you can backup the data,your settings, a list of manually installed packages, and move those to a fresh install fairly easily.   It is smart to have this down, since it also is a sufficient backup for emergencies when the storage fails.

**Aptik** is the tool for this, but there are others that provide more control at the price of higher complexity.
Start with aptik, see if that works perfectly for your needs.

---

### Post by oldfred on 2018-07-17
Easier to just reinstall & copy /home. If you changed a few system wide settings then those from /etc.
Only if server type applications may those be in various places in / (root).

If an Acer you have to enable "trust" from within UEFI on grub/Ubuntu .efi boot files in ESP - efi system partition.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

If you have drive plugged in with your install you want run this:
       
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lsutiger on 2018-07-17
> **TheFu said:**
> You can't, at least not easily.   But for a typical desktop, you can backup the data,your settings, a list of manually installed packages, and move those to a fresh install fairly easily.   It is smart to have this down, since it also is a sufficient backup for emergencies when the storage fails.

**Aptik** is the tool for this, but there are others that provide more control at the price of higher complexity.
Start with aptik, see if that works perfectly for your needs.

This looks like the right tool for the job, but the GUI is not installing correctly. I can call it by cli(which looks very complicated), but Ubuntu cannot find the program.
I'm receiving this when attempting to install:
Warning: mailcap line not starting with a media type in emerald
Problematic line:  application/x-emerald-theme; nametemplate=%s.emerald
I am currently in the out o the box Ubuntu login, not the gnome/compiz login

---

### Post by lsutiger on 2018-07-17
Read through the command switches. There is an easy --backup-all option! Backing up now!

---

### Post by yprezident on 2018-07-17
Try imaging your hard drive. Use the DD tool to make a copy of your image and put the image on the new hard drive. 

The new hard drive has to be the same size or bigger. 

And be careful with the DD tool you can destroy your data  ..

---


---
title: "Grub issues"
date: 2007-08-22
forum: General Help
---

### Post by Dhalimu on 2007-08-22
I have an HP Pavillion xt963 that I have been trying to install ubuntu on. After many problems with the CD Drive. (Installation died after erasing the hard disk, leaving me with neither Ubuntu or Windows.) I moved the HP hard drive to an E-machines computer, much newer and stronger (not all that strong though.)  I installed ubuntu on the HP Hard Drive as a slave, and upgraded to 7.04. However, when I try to move the HDD back to the HP, I cannot access windows (On the E-Machines hard drive) as it tries to load GRUB and then cannot. I do not need grub to run Ubuntu on the HP Pavillion, and it is detrimental on the E-machines. How can I remove grub from the e-machines computer?

---

### Post by merlinus on 2007-08-22
Use supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Directions:

[LIST=1]
[*]boot your SGD CD-ROM
[*]English Super [COLOR=#000000]Grub[/COLOR] Disk
[*] Windows
[*]Fix Boot of Windows[/LIST]         -merlin

---

### Post by Dhalimu on 2007-08-23
That does not really address what I need to do. I need to remove grub from the Windows Hard Drive.  And then I suppose I need to restore the normal Windows XP bootloader.

[INDENT]GNU/Linux is installed in your pc, you reinstall Windows and GNU/Linux no longer boots as Grub menu no longer appears on boot. You can restore Grub on your MBR automatically.
You have Windows installed in a second hard disk and it does not want to boot. If you swap it from Super Grub Disk you will be able to boot it.
You can not boot Windows because your MBR is corrupt or Grub installation is not well done or whatever. With Super Grub Disk you will be able to boot the partition where Windows reside.
No Active Partition Found message appears. With Super Grub Disk you can activate partitions.[/INDENT]

---

### Post by eggdeng on 2007-08-23
You need to use fixmbr. The simplest how-to I could find on Google is [http://askbobrankin.com/fix_mbr.html]("http://askbobrankin.com/fix_mbr.html")

---

### Post by Dhalimu on 2007-08-23
Can I use fix MBR if I am already in Xp? I can access Xp if I have both hard drives in.(The linux and the Xp) and I dnt have the recovery cd. So can i run fix MBR from a command prompt in XP if I am on an admin account?

thanks.

---

### Post by Dhalimu on 2007-08-23
I mean, if I run fixmbr in the command prompt in Xp while 2 HDDs are in, one with linux, one with XP. (Xp is the master) will that fix the XP boot issues?

---

### Post by eggdeng on 2007-08-23
> can i run fix MBR from a command prompt in XP if I am on an admin account?

Short answer: I don't know.

If what you want is to get the two OSs working on the same machine, I think you have to bear in mind that whereas linux will recognise and allow you to boot your XP partition, XP will not reciprocate this courtesy. This is why I would be inclined to 
a) first follow the steps in the fixmbr how-to to fix the XP MBR
b) then set the XP disk as slave and the linux disk as master
c) edit the /boot/menu.lst on this to allow you to chainload the XP partition
This last step is actually very simple, just do a google search for chainloading and you will find lots of resources.

---


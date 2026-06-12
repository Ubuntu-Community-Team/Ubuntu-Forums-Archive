---
title: "Uninstalling ubuntu feisty but keeping vista."
date: 2007-05-27
forum: General Help
---

### Post by G-Izzat on 2007-05-27
Hi there,guys.

I've been using ubuntu for 3 months now,but I've decided not to use it on my vaio sz43-gn notebook. I just bought the notebook which is vista pre-installed. I installed ubuntu and was happy with it. I did a partition for ubuntu using the vista disk management. But Vista to me is much better right now because I need to use it to do all my work.

I've a question and I hope you guys can help.
I need to uninstall ubuntu to have more space for Vista. I'll be installing ubuntu again when I get the money to upgrade my hard disk. GRUB detects Vista normally and I changed Vista to be first on the GRUB list.
May I know how to uninstall ubuntu without affecting Vista?

Thanks. Appreciate it.
:)

---

### Post by Ub1476 on 2007-05-27
Almost the way you made the space available for Ubuntu, just delete it instead. 

(right click, delete)

Next you can make the partition for Vista in full size. I don't remember how, but you'll find everything under the section: Disk Management.

About Grub, I think you need to replace it with Windows boot loader..

---

### Post by Rui Pais on 2007-05-27
> **Ub1476 said:**
> Almost the way you made the space available for Ubuntu, just delete it instead. 

(right click, delete)

Next you can make the partition for Vista in full size. I don't remember how, but you'll find everything under the section: Disk Management.

Deleting ubuntu partition will remove grub files too.

Its necessary to give some windows command from the install or restore Windows CD. I have no idea how that is done with Vista. With old  Windows it was fixmbr.

---

### Post by Ub1476 on 2007-05-27
> If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install EasyBCD. Go to “Manage Bootloader”, then “Reinstall the Vista Bootloader”, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.

Hope that works. Just drop the last part:p

---

### Post by G-Izzat on 2007-05-27
Thanks,guys. It worked! :)
I used the EasyBCD program and re-installed the bootloader.

---

### Post by DrAg0nBoY on 2008-01-17
Okey sorry for bumping this old thread but I wanted to ask something.

I am thinking of remuving Ubuntu, and instal Kubuntu. But now I need to first download the easyBCD program to fix the mbr. So when I install kubuntu will the GRUB be in charge again or will I have to play with the Vista bootloader to find Kubuntu?

---

### Post by Rui Pais on 2008-01-17
> **DrAg0nBoY said:**
> Okey sorry for bumping this old thread but I wanted to ask something.

I am thinking of remuving Ubuntu, and instal Kubuntu. But now I need to first download the easyBCD program to fix the mbr. So when I install kubuntu will the GRUB be in charge again or will I have to play with the Vista bootloader to find Kubuntu?

Hi
first you don't need to remove ubuntu to get kubuntu. You can uninstall ubuntu-desktop and  after that install kubuntu-desktop. It should give you the same as an install from zero...

But if you want to install from CD anyway you shouldn't worry with such things... kubuntu install will reinstall grub on mbr and create a correct menu list with all OS found, including Vista. 

The problems appear when one installs first a Linux and after a Windows since Windows booter will overwritten grub boot on mbr and Windows installers don't care to search for other OS on disc ...


HTH

---

### Post by Laxrawr on 2008-04-08
Sorry to bump the thread again, but I have a very similar question. I want to uninstall Ubuntu Fesity Fawn but keep my Windows XP and the files on the drive. By the way, I have Ubuntu and Windows dual booted.
 I installed Ubuntu, loved it, had a beast of a time trying to get my internet up, but found out that it killed my internet on XP, which is where I do most of my work. I read the tip on "right click, delete", so I went to add/remove progams (in windows), but I couldn't find it. I am decent with windows, but I'm absolutley terribad with linux, so detailed instructions are appreciated. Right now Im off to see if I can install it via the cd. 

Thanks in advance.

---

### Post by strydermed on 2008-07-19
If you are stuck in a dual boot with Ubuntu/Vista or triple boot with Ubuntu/Vista/XP and want to remove Linux without affecting XP and /or Vista , there are many options..
If u have a Vista DVD, just boot off it and use the recovery console. Type *bootrec /fixmbr*
That's it you are done. If you don't have Vista DVD, then there are a few options. 
If you have deleted your Ubuntu partition from Windows you might that your system refuses to boot. Download Super Grub Disk and burn it to a cdrom, you can restore Windows after booting from that. 

ps: VistaBootPro does not work in this situation, but you can use it to do lots of other cool stuff.
If you can boot into Vista then, there is a easy way. Just follow the steps below:
1. Download MBRFIX.EXE from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) 
2. Put it in your C or D drive. It does not matter where. Now right click on it and select security tab. Make it "Run as Administrator"
3. Type cmd in vista search box in start menu and right click it and select run Run as Administrator. 
4. In the command prompt go the directory where u have MBRFIX and now type *MbrFix /drive [COLOR="DarkOrange"]0[/COLOR] fixmbr /vista /yes* . This wont work without administrator permissions. Replace 0 with the number of ur drive. Just leave it if u have only one hard disk
That's it reboot and Vista boot manager will be back in  place of Grub. Now you can go into Disk manager and format Linux partitions and reclaim the space

---


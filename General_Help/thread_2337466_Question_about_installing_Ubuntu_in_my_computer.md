---
title: "Question about installing Ubuntu in my computer"
date: 2016-09-18
forum: General Help
---

### Post by zandryz on 2016-09-18
Hello guys. I'm new to this forum and to Linux in general. I've created a Live USB with Ubuntu and I'd really love to install it along Windows 7. The problem is that I have both Windows 7 and Windows 7 Loader XE that appear in the Windows bootloader. My question is: if I install Ubuntu together with the previous operating system, do I get both Windows 7 and Windows 7 Loader XE in the Linux Grub or do I only get one Windows 7?

---

### Post by dragonfly41 on 2016-09-18
I don't personally know too much about installing with two versions of windows plus Ubuntu.  That sounds like a triple boot setup.   
I have a dual boot which works fine (I need to use Windows very occasionally).

But if you are experimenting with Ubuntu you have the option of starting with installing Virtual Box on windows and then installing Ubuntu as a virtual machine in Virtual Box.

---

### Post by RobGoss on 2016-09-18
Hello and welcome, From what I've read Windows 7 loader XE is something you use to get a un-licensed version of Windows, I know nothing about this so I can't advise so I don't know how that would play out as far as the boot loader goes

I can't speak for that XE loader but! if you choose to install **Ubuntu **along side **Windows 7**, you should be able to choose between Windows and Ubuntu with out any issues

---

### Post by zandryz on 2016-09-19
Alright, thanks for the replies! :)

> [COLOR=#000000]I don't personally know too much about installing with two versions of windows plus Ubuntu. That sounds like a triple boot setup. [/COLOR]

Yes, a kind of a triple boot with Windows 7, Windows 7 Loader XE and Ubuntu all of them appearing in the Linux bootloader. Is that possible?

---

### Post by oldfred on 2016-09-19
Are both Windows in primary partitions? And installs are BIOS/MBR?
Windows only boots from a primary partition. Normally second installs overwrite boot files in first installs boot partition whether separate 100MB boot partition or just one NTFS partition. That is the partition in Windows as "Active partition" and everyone else calls boot partition and has boot flag.

Grub does not use boot flag and cannot read BCD where Windows keeps info on installs. But you can reconfigure a second install if on a primary NTFS partition to also have boot files and then grub can directly boot both.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)

If UEFI, I do not know of a way to directly boot from grub.

---

### Post by zandryz on 2016-09-20
Well, there's only one partition and it doesn't boot with UEFI. Thanks for info anyway, I'll see what I can do! :D

---


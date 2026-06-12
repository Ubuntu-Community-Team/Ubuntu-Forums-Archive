---
title: "Linux AutoNeoGrub0.mbr is corrupt of missing?"
date: 2013-05-19
forum: General Help
---

### Post by LCBradley3k on 2013-05-19
[COLOR=#000000][FONT=Arial]I've been trying to get my windows boot manager working so I can boot both Windows 7 and Linux. Currently, I can boot both, but only run when I click on "Windows 7" in the boot manager (Linux will run if my external hard drive with it is plugged in).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I click on the Linux option I made with EasyBCD, it just says windows failed to start and the AutoNeoGrub0.mbr is missing or corrupt.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've already tried reinstalling Grub2 and giving it updates through the terminal. The same problem still remains.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Anything I can do to fix it?[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-19
I do not know EasyBCD.
       [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Did you install Ubuntu to the external hard drive, or did grub just get installed to the external drive's MBR? Grub auto installs to sda, and some computers promote an external drive to sda.

If you want grub in MBR to boot both systems.
      
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

### Post by LCBradley3k on 2013-05-19
> **oldfred said:**
> I do not know EasyBCD.
       [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Did you install Ubuntu to the external hard drive, or did grub just get installed to the external drive's MBR? Grub auto installs to sda, and some computers promote an external drive to sda.

If you want grub in MBR to boot both systems.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I installed Linux completely on the external hard drive (sdb), Windows 7 is on my internal hard drive (separately on sda).

Windows loads with a .efi and Linux with .mbr as I said.
Considering windows is .efi, is it even possible to boot both systems with MBR, how would that work?

I also just found out that EasyBCD doesn't work with UEFI (is that considered the same as EFI), sorry for the questions, I'm just starting out.
What should I do moving forward?

---

### Post by LCBradley3k on 2013-05-19
Also, here is the link I got from the summary:

[http://paste2.org/j2fEpD1k](http://paste2.org/j2fEpD1k)

---

### Post by oldfred on 2013-05-19
Since you have an UEFI system, you really need to install Ubuntu on second drive in UEFI mode. How you boot installer is how it installs.
UEFI also uses gpt partitioning.

The only way you can boot now is to go into UEFI and change to BIOS mode to boot Ubuntu and then go back and change to UEFI mode to boot Windows. Not an easy way to dual boot.

Some examples of two drive installs.
 Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by LCBradley3k on 2013-05-19
> **oldfred said:**
> Since you have an UEFI system, you really need to install Ubuntu on second drive in UEFI mode. How you boot installer is how it installs.
UEFI also uses gpt partitioning.

The only way you can boot now is to go into UEFI and change to BIOS mode to boot Ubuntu and then go back and change to UEFI mode to boot Windows. Not an easy way to dual boot.

Some examples of two drive installs.
 Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Okay, thanks a lot for your help. I think I will just stick with my current system, it sounds easier than everything else. If I want to run Windows, I just unplug my Hard Drive. Can't be chasing after perfection. ;)

---


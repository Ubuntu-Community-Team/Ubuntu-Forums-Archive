---
title: "Problem Running a Windows Partition in VMware"
date: 2008-05-29
forum: General Help
---

### Post by crazy_lazy_bear on 2008-05-29
Hello All,

     First, thank you to the moderators and all those who help out us noobs.

     To run a Windows partition in VMware, I followed [[COLOR="Blue"]_these instructions_[/COLOR]]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware"). Now, when I try to play Windows as a virtual machine in VMware, I receive the error "File not found: WindowsXP.vmdk". When I browse to ~/WindowsXP.vmdk, I receive the message: "Error while powering on: Cannot update snapshot data: Insufficient permissions". On the Windows side, I am running XP Pro.  On the Linux side, I am running Ubuntu Hardy. I have 1G of RAM. To install VMware in Hardy, I followed [_[COLOR="Blue"]these instructions[/COLOR]_]("http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804"). 

      Also, after configuring VMware, when I select the Windows partition from the GRUB menu, the next screen displays the Hardware Profile/Configuration Menu. From there, I can choose either The VMware or the Default profile.  Selecting either one will bring me to the Windows Log In screen.  Whichever Windows user I choose (work or home) will load Windows normally.  Here is some background info about my system:
     
     When I first installed Ubuntu, I used the instructions [[COLOR="Blue"]_found here_[/COLOR]]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html"). After installation, I had a problem with the GRUB loader. After selecting the Linux kernel, the GRUB loader would do nothing - I only had a black screen.  I burned the superGRUB utility to a CD and used that to fix the issue; however I don't know how I fixed it.  Now, upon startup, my system displays the GRUB menu before the boot.ini file settings from Windows.  (This seems backwards to me, because on my wife's system, the boot.ini file settings display before the GRUB menu.) For that reason, I deleted the line: "C:\UBUNTU.BIN="Ubuntu Linux"" from my boot.ini file.  In Gparted, the Windows partition is set as the boot partition.

     I would appreciate very much any suggestions as to where I went wrong as well how to resolve this issue.  Thank you for your help.

Jay

---


---
title: "WIN 8 GRUB-no loaded kernel"
date: 2013-05-12
forum: General Help
---

### Post by Xemnas2010 on 2013-05-12
I was trying to partition my hard drive to put win7 next to win8. I resized the main partition to create a 20gb unallocated space, however win7 refused to install saying format type was GTP or something to that effect. I quit the install and win 8 was still running, so I tried to add back the space I took.
now after the TOSHIBA logo pops up a GRUB command line shows up with this-[B][Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/flies completions]
[/B]
I've searched through a few forums already trying to find a solution and I'm coming up short. I found one that said to input command 'boot' and I got the message 'no loaded kernel.' I'm about to use a usb boot of ubuntu 12.11 to back up my important files if I can, but I still want to keep my win8 os. I still have the recovery partition intact and untouched. Is there a way to save my win8 os from grub? Or the livecd usb boot?

---

### Post by oldfred on 2013-05-13
If your Windows 8 was pre-installed then it is UEFI. And UEFI has to have gpt partitioning. And Windows only boots from gpt partitioning with UEFI, so you would have to install Windows 7 in UEFI. I have no idea if you can dual boot in UEFI, but have seen some convert Windows 8 to Windows 7. You have to use a flash drive and convert DVD installer to flash drive to make it UEFI capable. 

Both Windows & Ubuntu install in UEFI only if you boot flash drive in UEFI mode. Or they install in BIOS mode if booted from UEFI menu in BIOS mode using CSM/BIOS/Legacy or whatever.

Best to see details, Boot-Repair may offer to fix it, but lets review first.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

If you installed Ubuntu in BIOS mode, you may just need to go back and turn secure boot back on and boot Windows in UEFI mode with secure boot.

---


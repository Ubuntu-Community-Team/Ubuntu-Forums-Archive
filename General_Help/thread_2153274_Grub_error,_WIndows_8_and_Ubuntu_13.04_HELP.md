---
title: "Grub error, WIndows 8 and Ubuntu 13.04 HELP"
date: 2013-06-10
forum: General Help
---

### Post by pleasehelpp on 2013-06-10
[COLOR=#000000]I have Asus ux31a with Windows 8 preinstalled, UEFI of course. I have tried to install Ubuntu 13.04 and dual-boot it with Windows 8. Finally I managed to install Ubuntu by disabling Fast boot and Secure boot but the dual-booting was failing so I formatted with Windows D: in which I had Ubuntu installed. Later I tried to install Ubuntu again, Fast boot and Secure boot disabled. When I tried to install it, all I could get was a black screen so I turned the computer off and on again. Now my computer is saying:
```
error: unknown filesystem
grub rescue>
```
Nothing happens when trying to boot from liveUSB. I have tried this:
[/COLOR][COLOR=#414141][FONT=Arial][COLOR=#000000]```
grub rescue> set root=(hd0,0)
grub rescue>set prefix=(hd0,0)/boot/grub
grub rescue>insmod normal

```with hd0,0-6 but all I get is ```
error: no such partition

```
I guess it's because Ubuntu isn't existing anymore in my computer?
What can I do? I'd be happy to get both Windows 8 and Ubuntu 13.04.[/COLOR][/FONT][/COLOR]

---

### Post by oldfred on 2013-06-10
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

    
Did you follow this?
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also my signature for more info:

---

### Post by pleasehelpp on 2013-06-10
I'm downloading Boot Repair atm but I'm afraid the computer won't start the program as it won't run Ubuntu from liveUSB either. Do you have any advice for that?

---

### Post by oldfred on 2013-06-10
Did you change boot from UEFI to BIOS? Some also have an auto mode which may not be correct.

Do you have other boot entires when using your one time boot key. You may have both BIOS & UEFI entries.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by pleasehelpp on 2013-06-10
When I turned the computer on pressing esc and power button simultaneously I was able to choose Windows to open. Don't know yet how to get Ubuntu working but I'll follow the UEFI instructions. At least Windows is working now :)

---


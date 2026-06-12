---
title: "Installed xubuntu, now the computer doesn't turn on."
date: 2013-06-09
forum: General Help
---

### Post by the duude on 2013-06-09
I just installed xubuntu and clicked restart now.  The flash drive booted again and it said "try xubuntu" and "install xubuntu".  I held down the power button to shut the computer off.  WHen I tried turning it back on the power button lights up but I see nothing on the screen.

---

### Post by oldfred on 2013-06-09
If you can choose to boot flash drive in try xubuntu mode, run this. You should have a one time boot key to choose what device to boot or can change boot order in BIOS.

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

### Post by the duude on 2013-06-09
I can't see anything on the screen. It won't turn on.  THis won't work.

thanks anyway.

---

### Post by oldfred on 2013-06-09
You cannot even boot flash drive with one time boot key? Or get into BIOS?
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Some systems just get locked up after boot issues.
      
 Total cold boot with laptop
Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by the duude on 2013-06-10
wow, this actually worked.  Thanks a lot man.

---


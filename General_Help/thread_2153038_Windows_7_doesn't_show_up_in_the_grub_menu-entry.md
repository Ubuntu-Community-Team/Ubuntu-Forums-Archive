---
title: "Windows 7 doesn't show up in the grub menu-entry"
date: 2013-06-09
forum: General Help
---

### Post by bTanmay on 2013-06-09
Hello,
I have an ASUS K55V and i was running a dual boot Windows7 and Ubuntu 12.10 on it.
I upgraded my Ubuntu with the 
```
    sudo do-release-upgrade command 
```
When I rebooted my system the Windows 7 option showed up in the grub menu-entry but wouldn't work.
So i used the Windows 7 installation USB and executed the 
    ```

    bootrec \FixMbr
    bootrec \FixBoot
```
commands. Now the system reboots and shows up an error saying You should use  your Windows7  installation disc to repair Windows 7 startup.
I did so but the windows 7 option never showed up in the Windows 7 Installation USB list of installed OS.
So I used a live Ubuntu USB and used the boot-repair tool as suggested at ["]http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7), which worked fine and I got back my Ubuntu. Next I ran the ```
update-grub2
``` command in Ubuntu, but it did not  detect WIndows 7.
I've tried the suggestions given at
[http://ubuntuforums.org/showthread.php?t=1611877](http://ubuntuforums.org/showthread.php?t=1611877) 
[http://askubuntu.com/questions/110005/windows-7-doesnt-show-up-in-grub-after-installation](http://askubuntu.com/questions/110005/windows-7-doesnt-show-up-in-grub-after-installation) and
[http://askubuntu.com/questions/22629/add-windows-7-to-boot-menu](http://askubuntu.com/questions/22629/add-windows-7-to-boot-menu) .
But they didn't work either.

---

### Post by drascus on 2013-06-10
I would say try using Rescatux... Everytime I have had the kinds of issues you are having it has saved my ass. [http://www.supergrubdisk.org/rescatux/]("http://www.supergrubdisk.org/rescatux/")

---

### Post by oldfred on 2013-06-10
IF you already have Boot-Repair, post the link to BootInfo report so we can see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bTanmay on 2013-06-18
Hey my problem has been solved. Turn out there was a problem with my MBR and so i had to fix it manually using the **rebuildbcd** tool in windows.

---


---
title: "GRUB2 and dualbooting with Windows 7"
date: 2013-10-03
forum: General Help
---

### Post by LorDisturbia on 2013-10-03
Hello,
today I set up a dual boot with Ubuntu 13 and Windows 7 on a Samsung laptop. I have 2 HDDs: **sda **(1TB) had already Windows 7 on it; **sdb **(500MB) was clean. I managed to install Ubuntu on **sdb** via live-USB. After gathering some information, I understood that the two partitions I had to manually create where a root partition (mine is approximately 496 GB) and a swap partition (4 GB in my case). I also installed GRUB2 on sdb. Basically the idea was to leave windows untouched, and use windows boot manager (WBM) to chose which OS to boot.
Here came the first problem: I had succeeded in creating entries on WBM, but every time i chose Ubuntu I just went straight to the GRUB prompt. Being unfamiliar with Linux, I had no idea what to do from there. Eventually I managed to boot Ubuntu and I tried the boot repair to fix the GRUB prompt option.
This lead to the present situation: I know have GRUB2 installed on BOTH **sda** and **sdb**, and it loads regardless of the HDD boot priority I set. From there, I can choose either Windows or Ubuntu, and both work just fine (especially after deleting Ubuntu entries from WBM).

Now I have two questions:
[LIST=1]
[*]Is GRUB2 *supposed* to be installed on both device? Wouldn't it be cleaner if I had GRUB2 on **sdb** and WBM on**sda**?
[*]Is there any way to have GRUB2 loading ONLY if I choose to boot from **sdb** (by changing boot priorities in the BIOS), and having Windows loading directly (via WBM) if I give boot priority to **sda**?
[/LIST]

Thank you in advance for your help; I hope this was clear enough (unfortunately, I don't know much about linux and/or booting configuration)

P.S. If you need further information just let me know (and please tell me where to find it!)

---

### Post by oldfred on 2013-10-03
Boot-Repair likes to install grub2 to every drive, I prefer what you want or each drive has a separate install and its boot loader in the MBR of the same drive. Then if one drive fails you should still be able to boot from the other.

Boot-Repair can install a Windows type boot loader to sda. Just uncheck auto repair, and in advanced options choose which operating sytem to install to which drive. 
Or you can use your Windows repairCD or flash drive (you do have one?) to restore the Windows boot loader to sda.
Grub will let you dual boot easily so just set BIOS to default to sdb. Windows is not designed as a Boot Manager so it is a major work around to get it to boot Ubuntu.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Or from Ubuntu, this will install grub to sdb.
 sudo grub-install /dev/sdb

And this will install the lilo boot loader (boot loader only not all of lilo) to sda. Lilo works like Windows in booting from MBR.
      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

### Post by martinr on 2013-11-09
A new install worked more quickly for me.

Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR or vice versa.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

What did your HD structure turn out to be?

---


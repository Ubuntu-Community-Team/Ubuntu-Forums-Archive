---
title: "Booting problem"
date: 2013-11-09
forum: General Help
---

### Post by mathieu2 on 2013-11-09
Hello everyone!

This is my first post so I hope I am in the right section  :)

I had a dual boot (Ubuntu and Windows 7) fully fonctionnal since 1 year. Ubuntu and Windows 7 were installed on separated SSD Drives.

Today, I changed my SSD on witch Windows 7 was installed beacause it was broken. (my SSD with Ubuntu was unplug during the windows installation process).

After the installation, Windows 7 and Ubuntu were booting, but I needed to select the booting from the Bios since the link to Windows 7 in Grub was broken.

I made a live CD with boot-repair and I run the "Recommanded repair" to repair Grub.

Unfortunatly, I get this message when I reboot my computer :

error: file '/grub/i386-pc/normal.mod' not found

Can anyone help me?  Here is my URL boot-repair gave me :
[http://paste.ubuntu.com/6390199](http://paste.ubuntu.com/6390199)


Thank you and have a nice day!
Mathieu

---

### Post by oldfred on 2013-11-09
You will not be able to use grub to dual boot. You have Windows in UEFI boot mode on a gpt partitioned drive and Ubuntu on a MBR(msdos) partitioned drive booting in BIOS mode. The two modes are not compatible and once you start to boot in one mode you cannot switch, so grub cannot change mode to use UEFI.

You can reinstall Ubuntu in UEFI mode but have to reformat drive to gpt, and add an efi partition at beginning of drive.

Once you start using UEFI, generally best to make all drives gpt partitioned. Ubuntu will boot from gpt with BIOS, but Windows only boots from gpt partitioned drives with UEFI. And both Windows & Ubuntu only boot from MBR partitioned drives with BIOS mode.

You can boot by going into UEFI and turning on or off UEFI/CSM to match system's install mode. Some auto switch but you can only dual boot from BIOS or one time boot key.

---


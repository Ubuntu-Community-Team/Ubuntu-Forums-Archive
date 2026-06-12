---
title: "Installing firmware on Lenovo T590 deleted GRUB menu or removed from UEFI"
date: 2020-08-20
forum: General Help
---

### Post by abcuser on 2020-08-20
Hi,
on my laptop Lenovo T590 I have a dual boot Windows 10 and Ubuntu 20.04. GRUB menu was installed by Ubuntu install and Ubuntu and Windows can be selected from menu.

In Ubuntu 20.04 I have today started Ubuntu Software installation program and clicked on Updates. There was new firmware available to install. I have selected it and installed it. Reboot was required and after reboot no more GRUB menu displayed and Windows 10 automatically booted.

How to get back Ubuntu 20.04 system (and my data on it)?
Regards

---

### Post by CelticWarrior on 2020-08-20
That firmware update likely was an UEFI update and as any such updates do it reset the UEFI settings.
Just open UEFI settings > Boot menu (or similar), find out where's the setting for boot order and where "Windows bootloader manager" is replace it with "Ubuntu".

---

### Post by abcuser on 2020-08-21
I have searched the UEFI and can't find Ubuntu boot loader. I have sorted boot menu that every device should be executed BEFORE Windows boot menu, but Windows still starts up automatically.

Any other idea?
[ATTACH=CONFIG]286777[/ATTACH]

---

### Post by abcuser on 2020-08-21
I have manage to solve the problem. Solution to my problem is on: [https://superuser.com/questions/1247300/how-to-make-uefi-bios-start-grub-not-windows](https://superuser.com/questions/1247300/how-to-make-uefi-bios-start-grub-not-windows)

In Windows start Command Prompt with "Run as Administrator" the execute two commands:
[HTML]bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi
bcdedit /set "{bootmgr}" description "ubuntu"[/HTML]
and then reentering UEFI boot and set "ubuntu" as first selection, save boot settings and reboot. See attachment.

Now GRUB menu appears with Ubuntu and Windows selections. Tested and both operating systems boot normally. Problem solved.
[ATTACH=CONFIG]286780[/ATTACH]

---


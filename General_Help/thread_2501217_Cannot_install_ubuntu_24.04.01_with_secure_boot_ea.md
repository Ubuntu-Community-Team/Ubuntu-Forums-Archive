---
title: "Cannot install ubuntu 24.04.01 with secure boot eabled on lenovo thinkpad laptop"
date: 2024-09-27
forum: General Help
---

### Post by zuku on 2024-09-27
Hi,
I have a problem installing ubuntu 24.04.01 on the lenovo laptop thinkpad t14s gen5, no matter how I create bootable usb in rufus all the time I have error:
Secure Boot Violation
Invalid signature detected
Check Secure Boot Policy in Setup.

So i have disabled secure boot installed ubuntu alongside with windows 11, then rebooted enabled secure boot and again have he same error.

---

### Post by yancek on 2024-09-27
If you disable Secure Boot in the BIOS can you boot Ubuntu?  If so, try running the command in the last post at the link below, then reboot and access the BIOS and re-enable Secure Boot and try rebooting both windows and Ubuntu.

[https://forums.linuxmint.com/viewtopic.php?t=397115](https://forums.linuxmint.com/viewtopic.php?t=397115)

---

### Post by zuku on 2024-09-28
If I enable secure boot this error appear and after a while Windows is booting.
If is disabled then grub appears with option to boot Ubuntu/windows and both are booting.

---

### Post by oldfred on 2024-09-28
lenovo may have additional UEFI settings to secure boot.
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

Lenovo T14 is update to ThinkPad T400, T410, T420, T490. series, so issues may be similar.

---


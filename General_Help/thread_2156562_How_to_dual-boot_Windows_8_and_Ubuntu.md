---
title: "How to dual-boot Windows 8 and Ubuntu"
date: 2013-06-22
forum: General Help
---

### Post by Humps on 2013-06-22
Hi everyone,

I am currently running one of the latest versions of Ubuntu, but I need Windows, and am not ready to give up Linux.

I tried to burn ISO files of windows 8, but Xfburn and the other softwares don't work. There is always an error and the disc is ejected (I tried with a lot of different DVDs, and they all had enough space)
I can't find a way to burn it on a USB drive. The only way I can burn on a USB is to burn Linux, not windows.


Can anyone help me?

---

### Post by sgage on 2013-06-22
> **Humps said:**
> Hi everyone,

I am currently running one of the latest versions of Ubuntu, but I need Windows, and am not ready to give up Linux.

I tried to burn ISO files of windows 8, but Xfburn and the other softwares don't work. There is always an error and the disc is ejected (I tried with a lot of different DVDs, and they all had enough space)
I can't find a way to burn it on a USB drive. The only way I can burn on a USB is to burn Linux, not windows.


Can anyone help me?

If you have access to a Windows machine, you can use Microsoft's own USB burner, which is strangely called the "Windows 7 USB DVD Download Tool". It is available free on their website. It works fine for Windows 8 iso's as well as Windows 7.

Actually, I seem to recall that I've had success with unetbootin, which you can install from the stock Ubuntu repos.

After you install Windows, it will own the MBR, so if you want to dual boot you'll have to boot with a LiveCD, chroot to your Ubuntu system, and run grub-install. You can run 'grub-install /dev/sda' to put it on the MBR, or 'grub -f /dev/sdax', where 'x' is your Ubuntu system's partition. In that case you'll need some way to put an entry for Ubuntu in the Windows Boot Manager. EasyBCD is free and excellent for this purpose.

---


---
title: "Help restore grub for dual boot"
date: 2018-04-02
forum: General Help
---

### Post by elliotn on 2018-04-02
I need help, my laptop a hp 250 gas Windows 10, I installed ubuntu but in the process deleted the Efi partition. So windows couldn't boot and couldn't show up in grub. So I worked hard to restore the EFI partition and succeeded but lost grub so now I can only boot to windows 10 only, easybcd doesn't work. 

I know the ubuntu 17.10 partition is still there. 

Please help. I also tried to restore grub via a livecd but it didn't work

---

### Post by oldfred on 2018-04-02
If you totally reinstall grub, it will recreate the entries in the ESP.
Probably easier to use Boot-Repair, but you can chroot into your install and run the re-install from there.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If still issues, post link to the summary report from Boot-Repair.

---

### Post by elliotn on 2018-04-02
Thanks will try that

---

### Post by elliotn on 2018-04-02
> **oldfred said:**
> If you totally reinstall grub, it will recreate the entries in the ESP.
Probably easier to use Boot-Repair, but you can chroot into your install and run the re-install from there.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If still issues, post link to the summary report from Boot-Repair.

> **elliotn said:**
> I need help, my laptop a hp 250 gas Windows 10, I installed ubuntu but in the process deleted the Efi partition. So windows couldn't boot and couldn't show up in grub. So I worked hard to restore the EFI partition and succeeded but lost grub so now I can only boot to windows 10 only, easybcd doesn't work. 

I know the ubuntu 17.10 partition is still there. 

Please help. I also tried to restore grub via a livecd but it didn't work

Thanks it worked

---


---
title: "Dual boot Win10 and Linux --&gt; how to choose which one will be booting"
date: 2022-12-03
forum: General Help
---

### Post by lordjester on 2022-12-03
Hello all! I would like to beg for help!
I'm no newcomer to Linux. I have been using Linux for a few years now but on my laptop. Now I installed Ubuntu on a spare SSD. I would like to choose on boot which OS I want to boot into, WIN10 or Ubuntu. But I don't know how, besides pressing F11 and going into the boot menu order. I would like to have some kind of list of possible OS-es at the start, so I can choose which one I want. 
I google it, and I saw grub would do that for me if the Linux is on the same SSD as WIN, but it's not. Can anyone know the solution, if there is any?
Thank you so much!

---

### Post by dragonfly41 on 2022-12-03
There are several ways I have tried ..

This blog describes running efibootmanager

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

But frankly my preference (probably the minority view) is to install rEFInd alongside the standard EFI grub installation. You can install both. Read it up at its site.

The choice (list) is in a GUI and you can customise the style.

P.S. search at least @OldFred threads on this topic. Plenty of material to study.

---

### Post by lordjester on 2022-12-03
Thank you! I will look it up! Cheers mate!

---

### Post by oldfred on 2022-12-03
Grub does not have to be on same drive. 
It will offer to boot any other system installed on any drive.
But installs have to be in same boot mode, all UEFI or all BIOS.
And grub only boots working Windows. Or Windows cannot be hibernated/fast start up nor need chkdsk. Then you have to directly boot from UEFI or if Windows really broken may need your Windows repair/recovery flash drive or yoru backup to restore.

What does this show?
sudo update-grub

I also have used rEFInd, but primarily for emergency boot. It is so small, that I was able to use an old 256MB flash drive, long ago retired as too small for much.

---

### Post by mIk3_08 on 2022-12-04
> **lordjester said:**
> Hello all! I would like to beg for help!
I'm no newcomer to Linux. I have been using Linux for a few years now but on my laptop. Now I installed Ubuntu on a spare SSD. I would like to choose on boot which OS I want to boot into, WIN10 or Ubuntu. But I don't know how, besides pressing F11 and going into the boot menu order. I would like to have some kind of list of possible OS-es at the start, so I can choose which one I want. 
I google it, and I saw grub would do that for me if the Linux is on the same SSD as WIN, but it's not. Can anyone know the solution, if there is any?
Thank you so much!
I agree with  		dragonfly41 refind boot loader can help with this issue. Other great apps like rEFInd Boot Manager are EasyBCD, Clover EFI bootloader, OpenCore and rEFIt and etc. Regards and cheers

---

### Post by grahammechanical on 2022-12-04
I agree with oldfred

Use the UEFI settings to set the Ubuntu SSD with the boot priority and then load Ubuntu and run

```
sudo update-grub
```

If the print out show that Windows has been detected a reboot should give you the menu that you want

Regards

---


---
title: "How to make a Windows bootable USB installer?"
date: 2020-10-11
forum: General Help
---

### Post by keolynyk on 2020-10-11
I tried dd command and ether software but none of them worked. The USB drive is simply not recognized a bootable device when trying to boot from it.

---

### Post by CelticWarrior on 2020-10-11
Either find a Windows computer and do it online with the official Media Creation tool (easiest option) or in Ubuntu you can use MKUSB or WoeUSB.
The current crop of Microsoft ISOs has some deviations from the standard so a tool that's aware of that must be used, dd won't work.

---

### Post by C.S.Cameron on 2020-10-12
Mkusb-plug worked the best for me.
Mkusb-Dus also worked.
WoeUSB did not work.
Dd did not work.
Ventoy did not work in BIOS mode.

See: [https://askubuntu.com/questions/1274878/make-windows-10-bootable-usb-in-ubuntu/1274975#1274975](https://askubuntu.com/questions/1274878/make-windows-10-bootable-usb-in-ubuntu/1274975#1274975)

---

### Post by joniess101 on 2020-10-12
> **keolynyk said:**
> I tried dd command and ether software but none of them worked. The USB drive is simply not recognized a bootable device when trying to boot from it.

Etcher has also failed me many times.In comparison,about making a Windows bootable USB installer,i prefer iMgburn, ISO to USB,because of their simple operation steps.
iMgburn - [https://www.majorgeeks.com/files/details/imgburn.html](https://www.majorgeeks.com/files/details/imgburn.html)
ISO to USB - [https://iso-to-usb.en.softonic.com/](https://iso-to-usb.en.softonic.com/)
BTW,the USB is not recognized on the computer,the following article may help you in this regard.
[https://www.passgeeker.com/usb-device-not-recognized-on-windows.html](https://www.passgeeker.com/usb-device-not-recognized-on-windows.html)

---

### Post by oldfred on 2020-10-12
The latest versions of Windows changed to make the .wim file over 4GB. So now it cannot be directly installed to a FAT32 partition for UEFI boot as it is larger than FAT32 supports. Most directions on Internet are older and are before the .wim file became too large. 

The Windows installer splits the .wim file into two parts to allow it to fit in FAT32.

Windows ISO is not configured as the hybrid bootable DVD/flash drive configuration. So any tool that used dd will not work.

---

### Post by dragonfly41 on 2020-10-12
I believe that Rufus does that with .WIM > 4GB.
[https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows](https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows)

---

### Post by C.S.Cameron on 2020-10-12
> **dragonfly41 said:**
> I believe that Rufus does that with .WIM > 4GB.
[https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows](https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows)

I believe that a Rufus Windows installer is UEFI only.
It refused to boot Windows Installer on my old PC.
Of course this is probably okay for those with a UEFI computer.

---

### Post by keolynyk on 2020-10-14
> **oldfred said:**
> The latest versions of Windows changed to make the .wim file over 4GB. So now it cannot be directly installed to a FAT32 partition for UEFI boot as it is larger than FAT32 supports. Most directions on Internet are older and are before the .wim file became too large. 

The Windows installer splits the .wim file into two parts to allow it to fit in FAT32.

Windows ISO is not configured as the hybrid bootable DVD/flash drive configuration. So any tool that used dd will not work.

Never have the chance to unpack the ISO and no one mention this. 

p.s do you know any solution to fix this?

---

### Post by CelticWarrior on 2020-10-14
How many more solutions do you need?

---


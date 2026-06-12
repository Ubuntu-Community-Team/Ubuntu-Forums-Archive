---
title: "how to create a portable ubuntu usb?"
date: 2020-10-19
forum: General Help
---

### Post by shiaa67 on 2020-10-19
[COLOR=#242729][FONT=Arial]can I run ubuntu from usb on any other computer? like the Windows To Go drive.  it seems there is no softwares or tools that can copy ubuntu ISO to USB as portable. I konw how to burn iso to usb as a bootable installer, but that's not what I need, I need a portable ubuntu usb. any suggestion? 


[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-10-19
Welcome.

Just install Ubuntu normally to the USB drive or burn the ISO as "live with persistence".

---

### Post by ActionParsnip on 2020-10-19
Just install to the USB. The physical media is absolutely irrelevant to Ubuntu. Just remember to put GRUB on the USB stick so it'll boot.

---

### Post by HermanAB on 2020-10-19
Even easier:  Use the install USB widget as is and save your data on another USB widget.

---

### Post by shiaa67 on 2020-10-19
> **ActionParsnip said:**
> Just install to the USB. The physical media is absolutely irrelevant to Ubuntu. Just remember to put GRUB on the USB stick so it'll boot.

[COLOR=#242729][FONT=Arial][FONT=inherit]
Thanks, I've heard that Grub2 can boot directly from ".iso" images, so I'm hoping Grub2 will make it easy to drag-and-drop several "liveCD" iso images onto a bootable USB stick and try them out. 

PS:  Another question,  I also tried using [rufus]("https://rufus.ie/") and [AnyWinGo]("https://www.sysgeeker.com/windows-to-go-creator.html") tool to create a protable Windows to Go drive, but it still not booting on another PC. Do I need to disable the securte boot option in the BIOS?[/FONT]
[/FONT][/COLOR]

---

### Post by shiaa67 on 2020-10-19
> **HermanAB said:**
> Even easier:  Use the install USB widget as is and save your data on another USB widget.

Hello, what's the install USB wideget? can you give me details? I am a linux novice&#65281;

---

### Post by oldfred on 2020-10-19
Many names for USB flash drives or thumb drives. Widget, I assume is just another one.

There is the live installer, the live installer with persistence to save some data & full install. 
Do you want UEFI or BIOS bootable flash drive?
Some have created both, but makes it a bit more complex & can get out of sync with grub updates. I prefer to just have BIOS bootable flash drive and another as UEFI bootable. Since my systems are now mostly UEFI, I have mostly UEFI bootable flash drives. With my larger flash drives, I typically do a full install & add some ISO to boot for repair or install purposes.

If you want to directly boot ISO, you can install grub2 and use grub2's loopmount to boot many (but not all) ISO.
There are tools that automate that also.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
examples
[https://gist.github.com/Pysis868/27203177bdef15fbb70c](https://gist.github.com/Pysis868/27203177bdef15fbb70c)
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

 How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images, manual grub install
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)

---

### Post by C.S.Cameron on 2020-10-19
If you want to drag and drop ISO images onto your USB have a look at Ventoy: [https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html) It will also support persistence for Debian based OS.

I prefer mkusb for a working Persistent USB but it is designed to support just one OS at a time, (but can be modified to multiboot).

---

### Post by C.S.Cameron on 2020-10-19
Oops, double post.

---


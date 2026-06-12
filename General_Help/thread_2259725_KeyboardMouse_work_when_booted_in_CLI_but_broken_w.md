---
title: "Keyboard/Mouse work when booted in CLI but broken when desktop GUI starts"
date: 2015-01-06
forum: General Help
---

### Post by mrJTparadise on 2015-01-06
Hey guys - quick question.

I have a machine with Ubuntu 14.04 Server installed and installed LXDE on it.  
```
apt-get install lxde-core 
apt-get install lxdm
```

If I boot directly to the command line my keyboard works fine, but if I do a "startx" or "service lxdm start" neither of my peripherals work - they become non-responsive.  The only thing working on the desktop login screen is the RTC and I can watch the seconds pass by..

I've done : 
```
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```

Still not luck.  Any suggestions or ideas? I've done a lot of searching but it either pertains to ArchLinux.

Thanks to all who take the time to read this.

JT

---

### Post by mrJTparadise on 2015-01-07
Stil having trouble getting the keyboard and mouse to work after running startx or service lightdm start.  I've installed the generic-headers as well - no luck.

```

root@server:~# dmesg | grep hid


[    6.688567] usbcore: registered new interface driver usbhid
[    6.689800] usbhid: USB HID core driver
[    7.767775] hid-generic 0003:0566:4002.0001: input: USB HID v1.11 Mouse [USB Mouse] on usb-0000:00:1d.0-1.3/input0
[    7.971668] hid-generic 0003:413C:2106.0002: input: USB HID v1.10 Keyboard [Dell Dell QuietKey Keyboard] on usb-0000:00:1d.0-1.4/input0

```

---

### Post by Bashing-om on 2015-01-07
mrJTparadise; Hello;

Check what you can do in bios;

I think it was our most respected contributor, Cavsfan, who gave this advise:
> 
His(Bashing-om) 1st post was confused with a desktop edition... Ubuntu Server does not use X11 at all, unless the user installs it.

The Server install iso is Linux kernel and so it the installed system. So the keyboard is BIOS to Grub2. Grub2 has kb and basic USB drivers.. Note that LILO doesn't recognized USB keyboards... Then hands off to kernel (kb drivers there also). Then if there are graphics layers, as in a desktop edition, then there are additional keyboard drivers in X11.

After installing Server edition on hundreds of server's... I can confirm that "some" server boards don't like a USB keyboard on the install disk. ...and not all BIOS'es will pick up a USB keyboard in post. USB support on the motherboards has layers... So you have more of a chance on picking up USB keyboard through one of the USB root hub ports than through the second layer or an extension...Those root ports are normally on the back of the motherboard, near the keyboard/mouse PS2 ports. Usually ports on the front of a PC are on a higher layer or on an extension. But those same ports do pick up when the kernel boots through the HID drivers.

I have 2 server boards here that are opposite and would only POST with a USB keyboard, but those are oddballs and not the norm. A ASUS and a Dell 960 server. Funny thing is I have 2 Dell 960 Servers and the other is fine/normal. But with both those 960's, the USB keyboard is not recognized in enough time to be able to get into BIOS Settings using a USB keyboard, so it doesn't recognize them early enough on those...

I have access to both PS2 and USB keyboards here, but I "do" a lot of dev testing. Traditionally, you are going to have more of a chance for success with a PS2 keyboard during POST and the early boot process. I get keyboards (both usb or ps2) for about $10 each at a Recycler. I also have USB/PS2 adapters for my USB mice and keyboards. They plug into the mouse/keyboard PS2 ports of the motherboard and the USB mouse or keyboard plug into them. 


[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mrJTparadise on 2015-01-07
Hello Bashing-om,

I've tried disabling/enabling USB legacy support and still no keyboard/mouse even if I have grub boot to desktop.  I do not have any PS2 ports on the system unfortunately.

I have a custom built kernel - do you think it may need to be reconfigured?

I feel like I am missing something simple since the keyboard works when booting into "text" (command line/server) mode but not in GUI mode.

---

### Post by Bashing-om on 2015-01-07
mrJTparadise; Humm ...

Have you insured that "plug and play" is enabled in bios ? 'buntu is a fully "plug and play" compatible.

I think - and others can advise better - that the driver used in the 'text' mode may be different than that of the GUI, As the GUI is that higher layer .

Might find some relevant info as the what Xorg is doing about the keyboard in the system file " /var/log/Xorg.0.log " .

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]see what the system instructs
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


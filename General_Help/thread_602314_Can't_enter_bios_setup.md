---
title: "Can't enter bios setup"
date: 2007-11-04
forum: General Help
---

### Post by kernel1 on 2007-11-04
Hi guys. I have ubuntu 7.04 and Windows XP and I load ubuntu with grub. From the time that I installed ubuntu I can't enter bios setup before grub menu loads. I press F2 but I can't. It seems that is not working :(

I want to enter setup to change the configuration for my keyboard. Because I want to change this keyboard (usb wireless) with a simple keyboard non usb. 

Why Non-USB keyboards are not working @ the boot of my pc? So thats the problem that I need to fix with Bios Setup.

Now I have connected and the 2 keyboards and only the usb is working @ the boot. But I cant enter the setup..

Please Help!!

Thanks

---

### Post by Soarer on 2007-11-04
Unbuntu won't have altered the BIOS set-up. Are you sure it is F2 to get into the BIOS? It could be <del> or <esc>.

Try hitting one or other of those *before* you get to the GRUB menu.

---

### Post by kernel1 on 2007-11-04
Yes I know that ubuntu is not changing boot setttings. But before the setup I entered OK. The key is F2 and the key is shown at the boot: "Press F2 to enter Setup" and I press but the Grub is loading :( 
I think that the grub is the prob.
Also I can't solve the problem with the keyboard.

---

### Post by kernel1 on 2007-11-04
I tried successfully to enter BIOS Setup but with a USB Keyboard.

But I want to replace the USB keyboard with a classic PS/2 Keyboard. When I plugged the PS/2 I can't do it to work on boot...

Any ideas? I tried to find an option @ BIOS Setup but I can't find.

---

### Post by Soarer on 2007-11-04
BIOSs differ. Mine gives the option to use a USB keyboard, but the default is PS2 (ordinary connection). Some PS2 keyboards are actually USB-with-adapter-for-PS2 which may not work as a native PS2 k/b would.

Whichever it is, it's not Ubuntu as it happens before Grub loads. Could you try another PS2 k/b to see if that works, or look in the advanced settings of your BIOS (which may need a special code like <ctl>-F1 to activate)?

---


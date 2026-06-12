---
title: "Screen Resolution is all messed up"
date: 2007-06-19
forum: General Help
---

### Post by grathinam on 2007-06-19
Hi

when I started my laptop this evening, it did not load the graphical interface, but i was able to restore it.
uisng the following command from the terminal  -  sudo dpkg-reconfigure xserver-xorg

but the display is still  not very clear precisely not like what I had earlier, i tried to change this using screen resolution but it did not work.

Any ideas how to fix this

and also I want to know how do i find out what graphical card is in my laptop. I have IBM T41P

Thanks in advance

---

### Post by NeoLithium on 2007-06-19
In a terminal window you can use the command: ```
lspci
``` and it will list your graphics card.  Once you find that out, there could be a better graphics card driver that can be installed to get the most from the card :)

Just post back if you need a hand :)

---

### Post by grathinam on 2007-06-19
wow that was supersonic speed response, Thanks a lot really appreciate your help and find below the output from my terminal. 
ATI it is

Any recommendation or suggestion would be appreciated 

-----------------------------------

grathinam@IBM-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
**[COLOR="Blue"]01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)[/COLOR]**
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by NeoLithium on 2007-06-19
You bet, there's a few suggestions here for ATI drivers: 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by grathinam on 2007-06-20
My display is still not working as desired. I did try to change the screen resolution but which is not working either.

Find attached the screen print of the same.

My screen resolution is set to 1024 / 768, if i try to change to any higher resolution, it is breaking up.

any ideas how to resolve this

Thanks in advance

---

### Post by kusuriya on 2007-07-06
> **grathinam said:**
> My display is still not working as desired. I did try to change the screen resolution but which is not working either.

Find attached the screen print of the same.

My screen resolution is set to 1024 / 768, if i try to change to any higher resolution, it is breaking up.

any ideas how to resolve this

Thanks in advance
is it a widescreen mode?

---

### Post by Titi on 2007-12-21
i have the same problem as grathinam. i have a Acer Aspire 1660 laptop with widescreen. it happens when i change my resolution to 1280x800.
does anyone have a solution for this?
thanks!

---

### Post by Crafty Kisses on 2007-12-21
> **grathinam said:**
> My display is still not working as desired. I did try to change the screen resolution but which is not working either.

Find attached the screen print of the same.

My screen resolution is set to 1024 / 768, if i try to change to any higher resolution, it is breaking up.

any ideas how to resolve this

Thanks in advance

Have you tried Envy?

---

### Post by Titi on 2007-12-21
ok, i just tried envy, now i can't choose 1280x800 anymore :)

---


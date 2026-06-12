---
title: "Deleted ubuntu partition but kept the bootloader"
date: 2016-01-29
forum: General Help
---

### Post by imtheworstatthis on 2016-01-29
Hi guys! As said on the title, I had ubuntu installed on my pc (windows 8.1) and I could dual boot successfully. But i got tired of it since i never used ubuntu, so i decided to erase the linux partition. Everything was fine until the grub prompt appeared after i rebooted my pc (yes, i'm an idiot. I didn't change the bootloader back to windows').

So far i've tried: 
[LIST]
[*]Booting with a live ubuntu DVD and a USB but nothing happens. (Is there a command for this to work?)
[*]Tried booting windows with the chainloader command and got the message "invalid EFI file path"
[*]Created a recovery drive but it didn't work (thought about creating a recovery disk but you can't create one in windows 8.1 :D)
[/LIST]

Guys I don't know what else to do :?[CENTER][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/CENTER]
**[SIZE=1]pls send help[/SIZE]**
**[COLOR=#000000][FONT=Ubuntubeta]thanks [/FONT][/COLOR]**

---

### Post by Dennis N on 2016-01-29
To boot from live media, you need to open the one-time UEFI boot menu, and select what to boot. But Windows should also be an option on that menu. When you boot up, watch for information on what key to press to get it. On my system, it is F8, but this varies.

You can also go into the UEFI firmware to get a UEFI boot menu. Another key pressed during startup gets into that system. On mine it is DEL.

---

### Post by imtheworstatthis on 2016-01-29
Well... that wasn't that hard :oops:
Managed to change the boot priority and now it's working perfectly :p

Thank you very much!

---

### Post by Dennis N on 2016-01-29
Glad you got it working. Being able to do this is one of the nice benefits of UEFI. If you had an old BIOS install, you would have a bigger problem.

---


---
title: "Wireless driver? Video Card driver?"
date: 2007-05-05
forum: General Help
---

### Post by cdiem on 2007-05-05
I'm a total noob, needing some help. Please, help me find the appropriate driver for my wireless and my video card. I have no idea which one it has to be from the lspci. In the manager for the networking, in Ubuntu Feisty, there's no wireless section at all; in ubuntu Edgy there was one, which could be configured. I think this is, because I don't have the driver needed. But I don't understand the output from the lspci (I'm totally noob). Please, help me. Here's the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0a:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0a:06.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
0a:06.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

Also, there's a box in my system settings, that I have checked - for the restricted drivers manager, saying that "INTEl (R) PRO/wireless 3945 network connection driver for linux" is in use; but I just cannot see any wireless networks in the network manager.
I also am not very sure what kind of a video card I'm using (though I'd like to know :)  - I just cannot understand whether I have the driver installed, or I need to install one).

---

### Post by Sef on 2007-05-05
> I also am not very sure what kind of a video card I'm using (though I'd like to know 

This is your video card:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

It's an integrated video chip.  In other words, it is part of your motherboard.

> I just cannot understand whether I have the driver installed, or I need to install one).

If you posted this message, while using Ubuntu then you don't need another driver.   If it was not working, you would not be able to boot up into the Desktop.

---

### Post by cdiem on 2007-05-05
Thanks for your answer. The main idea for me was to know if linux supported it - for instance, some games need drivers installed for the video card. I posted the previous one using ubuntu on my LAN at home. As for the wireless, I really have no idea how to connect, and if I have the right driver for wireless (if I have it, why cannot I see any networks?). But thanks, at least I know what my video card is now.

---

### Post by Thingymebob on 2007-05-05
> 04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)Is your wireless card

look here:
[http://ubuntuforums.org/showthread.php?t=387356&highlight=3945ABG]("http://ubuntuforums.org/showthread.php?t=387356&highlight=3945ABG")

---


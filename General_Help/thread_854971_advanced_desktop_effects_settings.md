---
title: "advanced desktop effects settings"
date: 2008-07-10
forum: General Help
---

### Post by jkid on 2008-07-10
im having problems making  advanced desktop effects settings to work(do the cube thing or anything) i  can initiate the prog but doesnt do anything[COLOR="Red"][COLOR="Red"][SIZE="5"][/SIZE][/COLOR][/COLOR]

---

### Post by jkid on 2008-07-10
read my treat

---

### Post by iaculallad on 2008-07-10
> **jkid said:**
> read my treat

And what thread would that be? This [one]("http://ubuntuforums.org/showthread.php?t=854971")? Try to patiently wait for member's replies and try not to open unnecessary threads, that won't help either.

---

### Post by jkid on 2008-07-10
the one about advanced destop effects

---

### Post by jkid on 2008-07-10
the one about desktop effects

---

### Post by jkid on 2008-07-10
help help

---

### Post by iaculallad on 2008-07-10
Install compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
```

Navigate to System->Preferences->Advanced Desktop Effects Settings, go to General Options, "Desktop Size" tab. Make sure "Horizontal Virtual Size" is set to 4. Then return to the main window, and enable the Desktop Cube and Rotate Cube plugins.

To spin the cube: Press Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and left-click and drag the screen/desktop.

---

### Post by jkid on 2008-07-10
yax yax yax a bunch but didnt solve the problem

---

### Post by jocko on 2008-07-10
What graphics card do you have?
Which drivers does it use?

---

### Post by jkid on 2008-07-10
dont really know my GC but my pc is a HP DV4000

---

### Post by jkid on 2008-07-10
fix it myself...was that the visual effects were set to best performence....but anyways yax to all

---

### Post by jocko on 2008-07-10
> **jkid said:**
> dont really know my GC but my pc is a HP DV4000
That doesn't help much. I tried to google for that laptop, but there appears to be several variants of it with different graphics cards...

Open up a terminal and run this command:```
lspci
```Paste the output here, so we can see what graphics card you have.

---

### Post by jkid on 2008-07-10
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



it says it is 915g or something

---

### Post by isaacj87 on 2008-07-10
> **jkid said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



it says it is 915g or something

I have the exact same chipset and it runs Compiz Fusion reasonably well. What exactly are you trying to do?

---

### Post by jocko on 2008-07-10
Ok, that's an intel graphics chipset. So the best drivers are already installed by default in ubuntu and as long as it's working you don't need to change anything.

---

### Post by kdcoetzee on 2008-07-10
Is all the desktop effect off, or is it just the cube that does not work ?

is your windows wiggly. when you minimize do they fade or shrink.

---

### Post by zvacet on 2008-07-10
@ **jkid**

You allready have thread open and now you want another one for same question.It is not how it works,because you make it difficult to people who want to help you,for yourself(you have to keep eye on few threads),and for others with similar problem.My advice will be to stick with your original post and be patiente.Somebody will help you.

---

### Post by jkid on 2008-07-10
[COLOR="Blue"]thanx again to all the threat helpers....the problem was that the visual effects were set to best performanc[/COLOR]e[COLOR="Blue"][/COLOR]

---

### Post by jkid on 2008-07-10
ok thank you

---

### Post by Berean on 2008-07-10
For future reference jkid, the following thread I found to be very helpful.
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633) Regards,

---

### Post by bapoumba on 2008-07-10
Threads merged.

---


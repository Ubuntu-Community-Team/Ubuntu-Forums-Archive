---
title: "[SOLVED] Check graphics card"
date: 2008-04-02
forum: General Help
---

### Post by waterskill on 2008-04-02
How do I chekc what kind of graphics card I have? I forgot and I need to know which drivers to install.

---

### Post by kesman on 2008-04-02
```

sudo lspci |more

```

---

### Post by waterskill on 2008-04-02
> **kesman said:**
> ```

sudo lspci |more

```

Thanks :)

---

### Post by waterskill on 2008-04-02
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML E
xpress Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (r
ev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
--More--
er #4 (rev 02)
--More--
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
--More--
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
--More--
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
--More--
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
--More--
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
--More--
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
--More--
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
--More--
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
--More--
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```

Is this a VGA?

---

### Post by chewit on 2008-04-02
VGA is the port for a screen cable. It is used to basically plugin your screen to your computer/graphics card

---

### Post by waterskill on 2008-04-02
Oh...lol..... 
Then what type is it? :S

---

### Post by lswest on 2008-04-02
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03)

that's your card, it's an Intel 945GM card, no restricted drivers required i believe in linux if that's what you're after.

---

### Post by Crafty Kisses on 2008-04-02
> **waterskill said:**
> How do I chekc what kind of graphics card I have? I forgot and I need to know which drivers to install.

```
glxinfo
```

---

### Post by waterskill on 2008-04-02
> **lswest said:**
> that's your card, it's an Intel 945GM card, no restricted drivers required i believe in linux if that's what you're after.

Oh okie doke thanks :)

---

### Post by lswest on 2008-04-02
no problem ^^ thanks for the thanks.

---

### Post by waterskill on 2008-04-02
> **lswest said:**
> no problem ^^ thanks for the thanks.

No problem. I thank whoever helps me out in any way :)

---


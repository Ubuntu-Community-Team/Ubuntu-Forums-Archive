---
title: "Can I run compiz?"
date: 2008-04-30
forum: General Help
---

### Post by darco on 2008-04-30
I have a Toshiba Satellite Laptop with the following specs:
Intel Core Duo 1.6ghz 2mb L2
Chipset Intel 945GM
2gig pc4200 mem
Intel intergrated Vid card 950

My question is, do I have enough oomph to run desktop effects? I ask because when I choose Normal from the Appearance tab, it reports that desktop effects cannot be enabled.
thxs
darco

---

### Post by klange on 2008-04-30
i945 will run Compiz easily, so that's not your problem.
Run 'compiz' in the terminal and post the output.

---

### Post by darco on 2008-04-30
I get this:

```

```Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Under Hardware drivers it does not show anythng,says no proprietary drivers are used...
I see another thread on this but no answers yet...
thxs
darco

---

### Post by klange on 2008-04-30
Strange, you sure it's a i950 and not a 960? 960 was blacklisted, last I checked (for problems I could have sworn *we* resolved). 945/950 is exactly what I use. Give me an lspci...

---

### Post by darco on 2008-04-30
> **WindowsSucks said:**
> Strange, you sure it's a i950 and not a 960? 960 was blacklisted, last I checked (for problems I could have sworn *we* resolved). 945/950 is exactly what I use. Give me an lspci...

Maybe Im wrong....

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by klange on 2008-04-30
Huh.
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
Well... Let's give this a shot: You can disable the whitelist check in the compiz starter script, I wouldn't suggest skipping all the checks, though. You can edit the function "running_under_whitelisted_driver()" so that the first line is "return 0" instead of LOG... (push the LOG part down a line.).
Try that and report any and all problems.

---

### Post by darco on 2008-04-30
is this correct?

# check driver whitelist
running_under_whitelisted_driver()
{
        "return 0"
	LOG=$(xset q|grep "Log file"|awk '{print $3}')

ran compiz...

 compiz
Checking for Xgl: not present. 
/usr/bin/compiz: 389: return 0: not found
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by darco on 2008-04-30
I took out the quotes....

compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by klange on 2008-04-30
Hm. Definitely driver problems, then.
You're going to need to check your Xorg.conf and ensure that it's the right driver...

---

### Post by darco on 2008-04-30
Ok...well thanks for your help,Ill see what I can do,,,I threw a Thanks at ya...

darco

---

### Post by darco on 2008-04-30
ok...so since I have nothing better to do (HH Released, Ibex in hiding) I went ahead and tried to get Compiz working on this laptop. I really only wanted to AWN...I added "intel" to the Xorg file which showed vesa...which actually helped. After reboot, my FF was scrolling like molasses...did this trick from before 
[http://grumpymole.blogspot.com/2008/03/ubuntu-hardy-intel-945-graphics-driver.html](http://grumpymole.blogspot.com/2008/03/ubuntu-hardy-intel-945-graphics-driver.html)
This was a fresh install and FF was fine so adding Intel to the xorg is still causing this bug....

AWN looks good, emerald running fine, I dont plan on adding much animation,,,,
good luck to others
darco


*edit* where did the "SOLVED" option go?

---


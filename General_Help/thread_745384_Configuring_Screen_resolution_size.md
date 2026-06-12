---
title: "Configuring Screen resolution size"
date: 2008-04-04
forum: General Help
---

### Post by kingofbigmac on 2008-04-04
I am actually using ubuntu on a live cd because my brother is being an *** and put a password on the computer.  I found the screen resolution part but I don't have either of the options I have a pretty wide setup here    1280 x 720 it looks jacked up with the setting I have now.  Is there an additional option to correct it or is there another linux version that I can use that will have the resolution I need.  Thanks alot. :guitar:

---

### Post by wolfen69 on 2008-04-04
open terminal and:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace to reset x.

---

### Post by tamoneya on 2008-04-04
What are you using for your graphics card.  Nvidia or ATI?  Either way you should go into the restricted drivers manager to start and install the driver.  Then if you have nvidia use ```
nvidia-settings
```

---

### Post by pytheas22 on 2008-04-04
Yes, if you have an nvidia or ATI card you will need to install the proprietary drivers to get full graphics effects.  But note that if you're only using the live CD, this won't work because you'll have to reboot.

Intel cards should work well out-of-the-box, since Intel has been kind enough to release open-source drivers, but sometimes there's still some tweaking required to get higher screen resolutions.

If you really want a higher resolution and can't figure it out, open a terminal and type the command

```
cat /etc/X11/xorg.conf
```

and post the output here so we can help you better.

But as I said, keep in mind that if you are not going to actually install Ubuntu to your hard drive, there may be no way to get a higher resolution while using the live CD.

---

### Post by kcnnc on 2008-05-08
This is the xorg.conf on my install, how do I change the resolution?

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "cn"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

---

### Post by pytheas22 on 2008-05-08
kcnnc, what kind of graphics card do you have?  It used to be listed in xorg.conf but apparently that's changed since Hardy.  If you don't know what your card is, post the output of:

```
lspci
```

then we can figure out what you need to do to get a higher resolution.

Also, are you able to use desktop effects (e.g. the cube, wobbly windows, et cetera)?

---

### Post by kcnnc on 2008-05-09
My lspci:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

---

### Post by pytheas22 on 2008-05-09
You have an Intel 945 video card, which should work pretty well.  Try running these commands:

```
sudo apt-get install xserver-xorg-video-intel
sudo apt-get remove xserver-xorg-video-i810
```

this will make sure that you're using the modern version of the Intel video driver, called "intel," instead of "i810," which is obsolete but still installed by default on Hardy (maybe for the benefit of people with older computers).

Let us know if this solves the problem (remember of course that you need to log out and back in again for the changes to take effect).

By the way, do you have desktop effects running?

---

### Post by kcnnc on 2008-05-10
After I swap the LCD monitor with a colleague, it was able to detect 1280x1024 on this monitor.

On the previous monitor the highest resolution to select was 1024x768. On Windows, this same monitor can do 1280x1024. 

I can't test further now but thank you very much, I had learned quite a bit with this exercise.

---

### Post by kcnnc on 2008-05-30
OK I encountered another of the same monitor.
Running these commands doesn't help.
```
sudo apt-get install xserver-xorg-video-intel
sudo apt-get remove xserver-xorg-video-i810
```

Any ideas?

---

### Post by pytheas22 on 2008-05-30
Sorry it's breaking again.  There's another strategy that you can try: use the i810 driver with the 915resolution hack.  You shouldn't have to do this anymore because the intel driver is supposed to be good, but the 915resolution approach should still work.  Until the release of Hardy, I used to have to use 915resolution in order to get full resolution on my Intel 945 video card and LCD monitor.  Try this:

```
sudo apt-get install xserver-xorg-video-i810
sudo apt-get remove --purge xserver-xorg-video-intel

```
Then follow the instructions [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29") for setting up 915resolution.  They're for Feisty but they should still work even in Hardy.  If you run into any trouble, come back here.

---

### Post by t52wa_r0x on 2008-06-17
Hi:
Don't mean to be rude, but would like to differ from what pytheas22 said above.
For Intel 945GZ, you really should stick with the newer "intel" driver.
Yes, the 915resolution method **does** work. But in my opinion, since your hardware is quite standard -- 17-inch non-wide LCD + Intel 945 -- the monitor should work properly with the "intel" driver so long as your "xorg.conf" file is set-up correctly. The 915resolution hack should be a last resort.


The standard "xorg.conf" for your case should be something like this (using the template you posted earlier):
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "cn"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes "1280x1024"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

If 1280x1024 does not work after this, the standard thing to do is to specify a modeline for 1280x1024 in "xorg.conf".
The standard command to do this is "gtf":```
gtf 1280 1024 60
```
The results:```
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```

Going back to "xorg.conf", you can see this section:
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
```

To use the modeline, insert it into the "Monitor" section like this:
```

Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
EndSection
```

After that, you should change the "Screen" section from **this**:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes "1280x1024"
EndSection
```
to **this**:
(Basically, enter the name of your modeline [e.g. "1280x1024_60.00"] in the "Modes" line.)
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes "1280x1024_60.00"
EndSection
```
Then, start your xserver. Hopefully, 1280x1024 works now.

---

### Post by kcnnc on 2008-06-18
Thanks for the suggestion, will try it when I can get my hand on the problematic monitor again.
The new monitors we are now ordering doesn't has this problem, which is good.

---


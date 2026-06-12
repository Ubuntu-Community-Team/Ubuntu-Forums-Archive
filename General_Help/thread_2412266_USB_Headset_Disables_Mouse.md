---
title: "USB Headset Disables Mouse"
date: 2019-02-10
forum: General Help
---

### Post by adamsglen93 on 2019-02-10
I have a Corsair HS70 Wireless Gaming Headset, and I am trying to get it to work in Kubuntu (18.04.1).


**The headset functions fine, with one caveat: whenever sound is played through the headset, the mouse is completely disabled. **This lasts for a few seconds after the sound stops. I've spent hours scouring online forums for similar issues and haven't been able to figure it out. Any help would be greatly appreciated.



**lsusb**

    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 008 Device 006: ID 1b1c:0a38 Corsair 
  Bus 008 Device 004: ID 046d:c332 Logitech, Inc. 
  Bus 008 Device 003: ID 046d:c338 Logitech, Inc. 
  Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I've tried adding every variation of this to the xorg config files in **/usr/share/X11/xorg.config.d**:

    Section "InputClass"
            Identifier "Corsair"
            MatchUSBID "1b1c:0a38"
            MatchProduct "Corsair Corsair HS70 Wireless Gaming Headset"
            Option "StartKeysEnabled" "False"
            Option "StartMouseEnabled" "False"
            Option "ButtonMapping" "0 0 0 0 0 0 0 0 0 0 0 0"
            Option "Ignore" "on"
    EndSection


Relevant bit from **libinput list-devices**

    Device:           Corsair Corsair HS70 Wireless Gaming Headset
    Kernel:           /dev/input/event6
    Group:            6
    Seat:             seat0, default
    Capabilities:     keyboard 
    Tap-to-click:     n/a
    Tap-and-drag:     n/a
    Tap drag lock:    n/a
    Left-handed:      n/a
    Nat.scrolling:    n/a
    Middle emulation: n/a
    Calibration:      n/a
    Scroll methods:   none
    Click methods:    none
    Disable-w-typing: n/a
    Accel profiles:   n/a
    Rotation:         n/a

---

### Post by him610 on 2019-02-10
> Bus 008 Device 006: ID 1b1c:0a38 Corsair 
Bus 008 Device 004: ID 046d:c332 Logitech, Inc. 
Bus 008 Device 003: ID 046d:c338 Logitech, Inc. 
They are all on the same bus. I don't know if it will work, but you might try installing them on different buses.

---

### Post by adamsglen93 on 2019-02-11
> **him610 said:**
> They are all on the same bus. I don't know if it will work, but you might try installing them on different buses.

Sounds reasonable. How would I do that?

Follow up question, no matter what USB port I use, everything is being assigned to Bus 08...

[FONT=monospace][COLOR=#000000]lsusb -t[/COLOR]
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 1: Dev 8, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 9, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 9, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 10, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 4: Dev 10, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 4: Dev 10, If 3, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 10, If 1, Class=Audio, Driver=snd-usb-audio, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M


Not sure if this is relevant (I know nothing about this), but this the motherboard manual: [/FONT]https://www.gigabyte.com/Motherboard/GA-970A-DS3P-rev-10#support-manual
The case that I have: [https://www.amazon.com/gp/product/B006TVQTHW/ref=ppx_yo_dt_b_asin_title_o04__o00_s02?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B006TVQTHW/ref=ppx_yo_dt_b_asin_title_o04__o00_s02?ie=UTF8&psc=1)

---

### Post by him610 on 2019-02-11
Your Corsair HS70 Wireless Gaming Headset looks like a nice headset. My setup is a little different with a Logitech wireless mouse, wired Dell USB keyboard, and a wired Blackwire USB headset; I have experienced no problems. I am also using Xubuntu LTS 18.04.

USB devices are sort of like a black box - either they work or do not work.
Other than your switching USB ports, or switching USB devices, I can think of no other possible remedies.
How did you come up with nine (9) USB buses? I only have two and one of those is a USB 3.0 hub.

---

### Post by Kris_M on 2019-02-12
I know the wireless mouse dongle has to be on a USB2 port, but even so I have sometimes seen this if I plug something like my mp3 player into it. Not doing it at the moment. Don't know why.

---

### Post by adamsglen93 on 2019-02-12
> **him610 said:**
> Your Corsair HS70 Wireless Gaming Headset looks like a nice headset. My setup is a little different with a Logitech wireless mouse, wired Dell USB keyboard, and a wired Blackwire USB headset; I have experienced no problems. I am also using Xubuntu LTS 18.04.

USB devices are sort of like a black box - either they work or do not work.
Other than your switching USB ports, or switching USB devices, I can think of no other possible remedies.
How did you come up with nine (9) USB buses? I only have two and one of those is a USB 3.0 hub.

I honestly have no idea why it shows 9 USB buses. I'm also confused because I have a Logitech G502 mouse, and G610 keyboard, both are supposed to use USB 2.0... but they only work in the USB 3.0 ports. I think the headset needs USB 3. Maybe that has to do with it? 

This is driving me mad, because it feels like something is not quite configured right. The headset/keyboard/mouse worked fine together on Windows (recently switched my gaming PC to Linux too, can't stand Win10 anymore), so the hardware capability is definitely there, and the headset does function perfectly in Kubuntu, it just also disables the mouse lol.

I don't know why I just thought of this, but I can also try plugging it into my laptop which is running Kubuntu 18.04.1 as well and see if I get different results.

---

### Post by adamsglen93 on 2019-02-12
Ok, so this headset works perfectly on my laptop which is running the exact same OS as the desktop machine. The mouse (and touchpad) work just fine at the same time.

Something must be wrong in the USB setup on my desktop.

---

### Post by adamsglen93 on 2019-02-12
I FOUND A FIX!!! :) Works perfectly now.

[https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370)




lsusb looks a lot more sane now too lol


[FONT=monospace][COLOR=#000000]/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M[/COLOR]
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    |__ Port 2: Dev 2, If 0, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 1, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 2, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 3, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M


This even fixed and issue I had with my secondary hard drive (unable to partition it/format it as ext4 or do much of anything with it). YESSSS

[/FONT]

---


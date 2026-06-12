---
title: "&quot;Smirched&quot; text in 13.10 font problem, some letters get unreadable until window switc"
date: 2013-10-25
forum: General Help
---

### Post by vasa1 on 2013-10-25
I'm starting this because there's another thread in Ubuntu +1. Users of 13.10 can feel free to post here and not worry about hijacking threads :)

I've been seeing one misformed letter per screen on Lubuntu 13.10 (clean install). It's mostly on Firefox beta. I'm not really sure if I've seen it with other apps. 

If I highlight the letter by dragging the mouse cursor over it, the letter becomes perfect again.

If I press printscreen, the letter becomes perfect.

If I scroll the line off the screen and then bring it back, the letter appears perfect.

---

### Post by ajgreeny on 2013-10-25
Could this be related to your settings for text rendering, wherever that is in unity.  Perhaps it is worth trying to change those settings in some way, particularly the **hinting** and **sub-pixel-order**

---

### Post by vasa1 on 2013-10-25
> **ajgreeny said:**
> Could this be related to your settings for text rendering, wherever that is in unity.  Perhaps it is worth trying to change those settings in some way, particularly the **hinting** and **sub-pixel-order**
I'm using Lubuntu + Thunar and xfdesktop. No Unity. I haven't knowingly made any changes re. hinting or sub-pixel-order or anti-aliasing.

It's quite rare, this one messed up letter on a screen, but I'll look out for whether it's only in Firefox beta or in other software as well.

---

### Post by ajgreeny on 2013-10-27
> **vasa1 said:**
> I'm using Lubuntu + Thunar and xfdesktop. No Unity. I haven't knowingly made any changes re. hinting or sub-pixel-order or anti-aliasing.

It's quite rare, this one messed up letter on a screen, but I'll look out for whether it's only in Firefox beta or in other software as well.

You may not have made any changes to hinting or sub-pixel order, but try editing the settings as I said before; maybe the OS default is not what is needed for your graphics card/monitor setup.

---

### Post by klarki on 2013-11-04
here's a screenshot, please help me. The letter "U" is unreadable. I noticed it for the first time in 13.10. 

[ATTACH=CONFIG]247552[/ATTACH]

---

### Post by klarki on 2013-11-04
it happens at random and the letters get good again after the window gets focus or looses focus, or when I select(highlight) the text. It can happen to any of the letters and it happens in gnome terminal and in browsers.

---

### Post by Impavidus on 2013-11-04
In my experience, garbled letters are usually (but not always) caused by graphics driver problems. That's because the rendered letters are cached in video memory. When the window loses focus it may change the colour of the letters, switching to a different set of cached characters. What graphics hardware do you have? Have you tried experimenting with different drivers, if available?

---

### Post by SantaFe on 2013-11-05
Been getting the same in Kubuntu after upgrading from 13.04 to 13.10.  So it's not just limited to Ubuntu I guess.

---

### Post by kh11162 on 2013-11-10
I also have this problem, on a Lenovo Thinkapd x200. What are you using OP?

---

### Post by klarki on 2013-11-15
I'm using Dell desktop optiplex 780. The problem is still occuring.

---

### Post by klarki on 2013-11-15
klarki@klarki-dell:~$ lspci 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)

---

### Post by vasa1 on 2013-11-15
> **Impavidus said:**
> In my experience, garbled letters are usually (but not always) caused by graphics driver problems. That's because the rendered letters are cached in video memory. When the window loses focus it may change the colour of the letters, switching to a different set of cached characters. What graphics hardware do you have? Have you tried experimenting with different drivers, if available?

I have this problem as well with Lubuntu 13.10: [http://ubuntuforums.org/showthread.php?t=2183584](http://ubuntuforums.org/showthread.php?t=2183584)

I didn't see any problem while on Lubuntu 13.04 on the same computer. The only difference is that this time I went for the 64-bit OS.

My computer is a Dell Inspiron 1545 laptop from 2008 with integrated graphics, AFAIK.

---

### Post by vasa1 on 2013-11-15
> **klarki said:**
> here's a screenshot, please help me. The letter "U" is unreadable. I noticed it for the first time in 13.10. 

OP, can you please explain how you managed to take the screenshot? If I press PrintScreen, the letter promptly gets properly shaped.

---

### Post by klarki on 2013-11-15
I just pressed printscreen and the letters were still garbled.

---

### Post by vasa1 on 2013-11-15
> **klarki said:**
> I just pressed printscreen and the letters were still garbled.
Okay, so maybe my problem is different.

---

### Post by ventrical on 2013-11-25
I think this bug may be fixed as I am the OP on the other thread from U+1. It appears from my own point of view that it may have had something to do with Intel graphics driver .

---

### Post by vasa1 on 2013-11-26
> **ventrical said:**
> I think this bug may be fixed as I am the OP on the other thread from U+1. It appears from my own point of view that it may have had something to do with Intel graphics driver .
The U+1 thread is here: [http://ubuntuforums.org/showthread.php?t=2183483](http://ubuntuforums.org/showthread.php?t=2183483).
Another thread is here: [http://ubuntuforums.org/showthread.php?t=2185741](http://ubuntuforums.org/showthread.php?t=2185741)

I've been using my laptop for a few hours after today's updates and all text appears normal now.

Today's updates:
```
Start-Date: 2013-11-26  07:28:24
Commandline: apt-get dist-upgrade
Upgrade: libquadmath0:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9), gcc-4.8-base:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9), cpp-4.8:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9), libgomp1:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9), libnautilus-extension1a:amd64 (3.8.2-0ubuntu2, 3.8.2-0ubuntu2.1), libgcc1:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9), update-notifier-common:amd64 (0.147, 0.147.1), update-notifier:amd64 (0.147, 0.147.1), nautilus-data:amd64 (3.8.2-0ubuntu2, 3.8.2-0ubuntu2.1), systemd-shim:amd64 (3+real-0ubuntu1, 4-0ubuntu0.13.10), libstdc++6:amd64 (4.8.1-10ubuntu8, 4.8.1-10ubuntu9)

```

---

### Post by mauricio_ville on 2013-11-27
I also have the same problem. Some time ago when I tryed I also wasn't able to take a screen shot, although today when trying agan I was able to do it. The details of my video card and display driver are the following:

# lshw -c video
  *-display               
       description: VGA compatible controller
       product: Cape Verde PRO [Radeon HD 7750]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:e0000000-efffffff memory:f7c00000-f7c3ffff ioport:e000(size=256) memory:f7c40000-f7c5ffff
  *-display
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)

---

### Post by philinux on 2013-11-27
This has been raised before - seems to have gone away for me now in 13.10

[http://ubuntuforums.org/showthread.php?t=2183584](http://ubuntuforums.org/showthread.php?t=2183584)

Threads now merged.

---

### Post by vasa1 on 2013-11-27
I'm sorry but it's back but somewhat less frequent :(

Today's updates:
```
Start-Date: 2013-11-27  07:22:05
Commandline: apt-get dist-upgrade
Upgrade: libgail-3-0:amd64 (3.8.6-0ubuntu2, 3.8.6-0ubuntu3), gir1.2-gtk-3.0:amd64 (3.8.6-0ubuntu2, 3.8.6-0ubuntu3), libgtk-3-bin:amd64 (3.8.6-0ubuntu2, 3.8.6-0ubuntu3), libgtk-3-0:amd64 (3.8.6-0ubuntu2, 3.8.6-0ubuntu3), libgtk-3-common:amd64 (3.8.6-0ubuntu2, 3.8.6-0ubuntu3)
End-Date: 2013-11-27  07:22:20

```

---

### Post by atrystan-gmail on 2013-12-02
I have had this problem since upgrading to Kubuntu 13.10. It does seem to be a driver issue. While troubleshooting, I found that if I change the resolution from where I had it (1360x768) to a lower one and then back up, everything displays perfectly.

Hardware:

Lenovo G550
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
        Subsystem: Lenovo Device [17aa:3a02]
        Kernel driver in use: i915

This problem never occured in 13.04, so it must be something introduced into a new version of the driver. I suppose that we'll have to wait for an update, unless someone can point us to a newer version?

In the meantime, I'll simply change the resolution once at startup and go from there.

---

### Post by eamarillo on 2013-12-26
Well, sorry for the bump. I have installed Xubuntu 13.10 32 bits and I was experiencing the problem with the text rendering in Firefox. Fortunately I suspect right with the driver acceleration. In earlier versions of Xubuntu I enabled manually SNA acceleration. Now, I manually enabled the old method, because it seems SNA came for default and it fails. I don't know why, if before there wasn't any problems.

The pc has an Intel gpu, G41 chipset. It's a celeron E3400.
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

Creating the xorg.conf file:
```

gksu mousepad /etc/X11/xorg.conf
```

whit the info:
```

Section "Device"
        Identifier "intel"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection
```

Now it's working flawlessly.

---

### Post by vasa1 on 2013-12-26
@eamarillo, please take a look at the Phoronix link Toz provided here: [http://ubuntuforums.org/showthread.php?t=2194616&p=12878393#post12878393](http://ubuntuforums.org/showthread.php?t=2194616&p=12878393#post12878393)

---


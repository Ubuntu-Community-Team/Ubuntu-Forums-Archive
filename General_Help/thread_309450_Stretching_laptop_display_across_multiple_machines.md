---
title: "Stretching laptop display across multiple machines"
date: 2006-11-29
forum: General Help
---

### Post by rainbowsheep on 2006-11-29
Greetings, fellow Ubuntu users.

I have two machines, both running Ubuntu Edge.  One's a laptop and one's a desktop with two monitors.

I do most of my work on the laptop.  But I want to be able to use the laptop machine on the two larger displays and be able to use all three displays at once, but be using the software programs on the laptop to drive everything.

I'm aware of the synergy product, but that requires that I use the desktop environment on both machines, while I only want to use the desktop environment on the laptop.

Thanks in advance for any help.  Let me know if I can clarify anything.

Joe

---

### Post by strabes on 2006-11-29
that process differs greatly depending on whether you use nvidia or ati. I know the fglrx driver includes bigdesktop functionality by default; I used to use it. to install ati card drivers, go [here](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) and use method 1. when you're done, you can type sudo aticonfig --help, and that will bring up a lot of options that you can use. One thing that was a pain for me was to get different resolutions on the monitors, cuz my laptop is 1440x900 and the other monitor was 1600x1200. I eventually figured it out so here's the pertinent parts of the xorg.conf i was using:

```

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "PairModes" "1440x900+1600x1200"
        Option      "Mode2" "1600x1200"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

---

### Post by rainbowsheep on 2006-11-29
I don't think I explained myself well enough.  The two large monitors are connected to a desktop machine.  My laptop doesn't have two DVI ports to connect directly connect the monitors.

Again, the mouse and keyboard and two displays are hooked up to the desktop machine.  But I want to be able to use the laptop's desktop and software on both the laptop and on the two larger displays (and hopefully be able to share the mouse and keyboard between the two).

---

### Post by giants_fan on 2006-11-29
You could do this easily by running ssh with x forwarding.  On your desktop, ssh (with the -X option, I think) into your laptop.  Then when you start firefox or something from the terminal, it gets run from your laptop, but displays on your desktop.

---

### Post by rainbowsheep on 2006-11-29
Yes, that would work somewhat.  But it doesn't "stretch" the display seamlessly across the three displays.  

Maybe it's not possible.  

(and anyways, if I have a copy of Firefox running on the laptop already, how would I get the laptop to start firefox on the desktop machine?  That would mean that two copies of firefox would be running)

---

### Post by Severun on 2007-11-30
I'm looking for the same thing.

I think...

Basically it's this.

I have two machines and I want them to work like the fglrx Big desktop, i.e. I can drag applications across from one to the other.

---


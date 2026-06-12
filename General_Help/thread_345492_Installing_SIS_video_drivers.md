---
title: "Installing SIS video drivers"
date: 2007-01-24
forum: General Help
---

### Post by PetePete on 2007-01-24
when running the openGL screensavers my laptop runs them very slow and jerky. I'm presuming this is because i havn't installed the correct video drivers for my laptop. Currently using the KDE config program its set to: 
Graphics card ; SIS
Driver: SIS

This is the output of my lshw
```

*-display
                description: VGA compatible controller
                product: 661/741/760/761 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                resources: iomemory:d0000000-d7ffffff
iomemory:dfee0000-dfefffff ioport:dc00-dc7f

```

i've looked for the 661 and other cards in the kde config program but they are not listed. 

what else can i do to get graphics working properly?

---

### Post by dgoadby on 2007-05-30
Hi Pete,

SNAP! I have a Siemens Esprimo and the graphics is SIS761. The video is fairly stable at 1024X768 but when I try 1280X1024 there are vertical venetian blinds on the screen. 

Previously I was using Suse 10.2 and this managed the video very well so there must be drivers out there somewhere. :(

Other than this problem I am very impressed with Ubuntu (7.04)

---

### Post by PetePete on 2007-05-31
i run mine fine at 1280x1024

Are you using the 'sis driver?

my xorg.conf says...

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        VideoRam        128000
        Option          "UseFBDev"              "true"
EndSection

```

then
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x800"
        EndSubSection
EndSection

```

---

### Post by helliewm on 2007-05-31
Try downloading SIS drivers from here:

[http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml)

This should solve your problem.

Helen

---


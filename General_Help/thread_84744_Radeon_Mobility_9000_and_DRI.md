---
title: "Radeon Mobility 9000 and DRI"
date: 2005-10-31
forum: General Help
---

### Post by shooz on 2005-10-31
Hello!

I have an up-to-date Breezy install and I just can't get DRI working on my Thinkpad t40p with a Radeon Mobility 9000 (lspci reports it as "ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02)").

Everything looks normal in my Xorg.0.log until it gets to this point:
```

(==) RADEON(0): Write-combining range (0xe0000000,0x4000000)
(II) RADEON(0): Dynamic Clock Scaling Disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
...
(this error repeats with node name up to /dev/dri/card254)
...
(II) RADEON(0): [drm] drmOpen failed
(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.


```

The Device sestion of my xorg.conf looks like:

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"AGPMode"	"4"
	Option		"AGPFastWrite"	"true"
EndSection

```

Not sure what else to try here.  My goal is to be able to have reasonable video speed with power management features (suspend/hibernate) working.  I don't really need 3D acceleration, but it would be nice.  Should I be using the binary ATI drivers?

Full versions of the files: [xorg.conf]("http://skrul.com/xorg.conf") [Xorg.0.log]("http://skrul.com/Xorg.0.log")

Thanks for any help!
cheers,
shooz

---

### Post by RikoW on 2005-11-01
Hi there,

I have the same ATI graphic chip under Breezy and spend the last few days quite some time trying to get DRI to work. The ATI binaries (fglrx) are not an option, if you want to hibernate/suspend. Breezy come back to life with a corrupted X display.

It seems, that my module section in xorg.conf looks slightly different than yours, also I think, the device section turns on most options needed for 3D by default:

```
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"

        SubSection "extmod"
                Option "Omit xfree86-dga"
        EndSubSection

        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
        # new stuff
        Load    "radeon"
        Load    "xtrap"
        Load    "drm"
EndSection

```

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
EndSection

```

For some time, I couldn't get DRI to work, even though the Xserver told me on start-up it was enabled. Reason was that I had the fglrx driver from ATI installed, which brings with it its own version of libGL.so, which apparently does not work with the radeon DRI. So, after removing the fglrx driver and, to make sure, re-installing libgl1-mesa I can hibernate/suspend and have reasonable 3d acceleration.

Hope, that helps!

Good luck,
                        Riko

---

### Post by P.-A. on 2005-11-01
I had the same problem. I don' t really know why. In hoary 3D acceleration was working out-of-box.

I have resolved this. You just need to load DRM module before the radeon one.

Add this in your /etc/modules files 
agpgart
intel-agp
drm
radeon

---

### Post by shooz on 2005-11-01
Thanks for the help!  I uninstalled the fglrx stuff, removed the extra stuff from my Device section, and added those modules to /etc/modues and my DRI is working:

```

# glxgears -iacknowledgethatthistoolisnotabenchmark
libGL: XF86DRIGetClientDriverName: 4.0.1 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error:
Can't open configuration file /etc/drirc: No such file or directory.
libGL error:
Can't open configuration file /home/steve/.drirc: No such file or directory.
6518 frames in 5.0 seconds = 1303.490 FPS
6402 frames in 5.0 seconds = 1280.271 FPS
6367 frames in 5.0 seconds = 1273.242 FPS

```

Hooray!

cheers,
shooz

---

### Post by none on 2006-03-06
I am having a simular problem dri isnt working and im not able to startx but i have a ati radeon xpress 200m. 

> I had the same problem. I don' t really know why. In hoary 3D acceleration was working out-of-box.

I have resolved this. You just need to load DRM module before the radeon one.

Add this in your /etc/modules files 
agpgart
intel-agp
drm
radeon 
I don't know how to add those to my /etc/modules.

---


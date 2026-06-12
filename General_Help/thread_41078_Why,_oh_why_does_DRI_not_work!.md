---
title: "Why, oh why does DRI not work?!"
date: 2005-06-11
forum: General Help
---

### Post by akinwale on 2005-06-11
I just upgraded to Ubuntu 5.04 using dist-upgrade. I uninstalled XFree86 and installed X.org, hoping this would solve the problem of DRI not working, but it still doesn't work, sadly.

Here are the relevant sections of my xorg.conf file:
```
Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection
...
Section "DRI"
	Mode	0666
EndSection

```


I get this in my Xorg.0.log file:
```
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3122) rev 3, Mem @ 0xd8000000/26, 0xde000000/24, BIOS @ 0xdfef0000/16
```

and after moving down a little, this:
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via"
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
```

I've searched through the forums and I still haven't found the solution. The only information I got was that DRI isn't implemented for the CLE266 chipset (which is what I am using). If this is so (a disaster, really), are there any workarounds? Or do I have to purchase a new video card instaed of using the integrated video chipset?

Thanks.

---

### Post by akinwale on 2005-06-12
*bump*?

---


---
title: "Via Unichrome and Compiz/General effects"
date: 2008-06-25
forum: General Help
---

### Post by Firehalk on 2008-06-25
I know that VIA makes the worse combination with Linux, but on my present computer I've it and unfortunately I can't change it now.

Well, I tried Ubuntu a while ago and Video was always my only real issue with it (because of my Via Unichrome Pro IGP video card). Now with the Final version of Hardy in my hands, I decided to try it back again. The difference is that this time i discovered this link:
 [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

There I downloaded some driver (which is not exactly to my card by what I saw), and tested it. The resolution is perfect now, the frequency (hz) too, but I still can't do anything "cool" on Ubuntu, such as change the desktop effects.

When I go to **Appearance ** -> **Visual Effects** and change to any of the 2 last options, I get the message: Desktop effects couldn't be enable.

So I tried to install compiz, and that compiz-check thing. I runned it, and I got:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
 Driver in use:         via
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Detected driver is not on the whitelist. 
```

I've read on README that came with the VIA driver, that I should put "via" on the whitelist. But even with it there, compiz-checker said that it's not.

```
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx via"
```

On my xorg.conf, the driver name is correct, it's "via":

```
Section "Device"
	Driver "via"
	VendorName  "VIA Tech"
	BoardName   "via"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection
```

I have no ideas of whatelse to do, so any suggestion/advice is appreciate.

Thanks

---

### Post by Kevbert on 2008-06-25
Unfortunately Compiz still does not work with the Via [unichrome]("http://forum.compiz-fusion.org/search.php?searchid=706778") card

---


---
title: "Setting Xorg resolution with no monitor attached"
date: 2005-10-21
forum: General Help
---

### Post by evil-boweevil on 2005-10-21
I have a ubuntu box without a monitor and I want to set it up so that X runs at 1024x768.  It works fine when there is a monitor attached, but when it's not attached X will default to 640x480.  Is there any way to force X to use a certain resolution even though it cannot probe for it?  The reason I want this is so I can VNC over to that computer with a usable resolution.  Thanks.

---

### Post by edwardog on 2005-10-21
If you ```
sudo nano /etc/X11/xorg.conf
``` and check under Section "Screen" -> Subsection "Display" -> Modes, which resolutions have you set?

---

### Post by evil-boweevil on 2005-10-21
Thanks for the response, but I managed to finally find the answer with a lot of searching.  I needed to add

HorizSync and VertRefresh values to the monitor section

and then

Option "NoDDCValue"  "True"

to the device section.  This will keep X from reverting back to 640x480.

The full explanation of this is here: [http://forums.gentoo.org/viewtopic-t-125384-highlight-resolution+640x480+monitor+attached.html]("http://forums.gentoo.org/viewtopic-t-125384-highlight-resolution+640x480+monitor+attached.html")

---

### Post by Franko30 on 2006-01-29
Hi,

First: Sorry for the crosspost, but resolving this was just too frustrating for me and I want people to find this in all the other unresolved "help VNC resolution" threads, too.

I didn't want to go for the modelines - and found a solution that works for me:

In the **device** section of the **xorg.conf** I changed the driver to

```
Driver		"vesa"
```

and finally my headless Ubuntu setup starts up in the required resolution of 1024x768 I entered in the xorg.conf file - which makes using this machine with VNC a bit nicer than with 640x480. :-)

And we don't need a fancy 3D driver on a machine accessed via VNC - do we?

It worked on two machines (running climateprediction.net with BOINC) with different graphics adapters.

I hope it might work for others, too...

Franko30

---


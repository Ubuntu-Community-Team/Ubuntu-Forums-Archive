---
title: "Accessing installed files via Live CD"
date: 2005-07-29
forum: General Help
---

### Post by Irony on 2005-07-29
I've installed xorg-driver-fglrx for my radeon card according to the instructions on [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

It says to change ati to fglrx in the xorg.conf file. I assume it means change the Driver "ati" section to Driver "gflrx"? i.e.

[PHP]from;

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 Pro (R420 JI)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

to;

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 Pro (R420 JI)"
	Driver		"gflrx"
	BusID		"PCI:1:0:0"
EndSection[/PHP]

However if this doesn't work and I can't boot to GUI, I would like to use the Live CD to change the /etc/X11/xorg.conf file back to what it was.

How do I actually alter the installed /etc/X11/xorg.conf file via the Live CD.

---

### Post by Irony on 2005-07-30
What I'm asking in a more general sense is how does one access and alter installed ubuntu files via the Live CD, in situations for example when the installed ubuntu won't boot into GUI.

---

### Post by Ptero-4 on 2005-07-30
[QUOTE=Irony]What I'm asking in a more general sense is how does one access and alter installed ubuntu files via the Live CD, in situations for example when the installed ubuntu won't boot into GUI.[/QUOTE]
 make a backup copy of your xorg.conf from your installed ubuntu, if your system fails to boot or won't load x11 you can boot from the livecd. go to places > system and open your ubuntu partition (I haven't done this before but I think that the LiveCD detects your installed ubuntu and mounts it's partition automatically) go to the etc folder next to the X11 folder and delete the damaged xorg.conf and move/rename the backup into place then reboot (eject the LiveCd before the computer tries to boot from it). Your system should be functional again.

---

### Post by Irony on 2005-07-31
Thanks Ptero-4 that is the sort of thing I was looking for. What I've done so far is;

[PHP]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup[/PHP]

This has created an exact copy of my xorg.conf file but with the name _backup stuck on it. I'll look for it later via the LiveCD. If I can find it I know that I can therefore just recreate the original xorg.conf file if I need to.

This is still new stuff for me so its quite fascinating seeing the terminal commands create files.

---


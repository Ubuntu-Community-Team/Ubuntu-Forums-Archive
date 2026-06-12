---
title: "VNC and missing fonts"
date: 2005-07-04
forum: General Help
---

### Post by gjaffe on 2005-07-04
Hi --

I have a problem with missing fonts when I connect to my ubuntu box with vnc.  When I sit at that machine and login from the console, I have twice as many fonts compared to connecting to that machine from VNC.

I tried putting the following in my /etc/vnc.conf file.

$XFConfigPath = "/etc/X11/xorg.conf";

so that the fonts (and everything else) would match my console.  This did not help.

I also tried to explicitly specify the font directories by placing a $fontPath line for each font directory specified in my xorg.conf file, and this also did not help.

I then installed and started xfs-xtt after making sure that the fonts in its config file matched the fonts in xorg.conf.  I took the $fontPath lines out of my vnc.conf file and replaced them with the single line

$fontPath = "tcp/localhost:7100";

Naturally, I killed and restarted the vncserver with each attempt.

None of this helped.  I tried this with both vncserver and tightvncserver.

Anyone have a clue of how to get the same fonts in my VNC sessions that I get when I login from the console?

Thanks,

Gary

---

### Post by SadaraX on 2005-10-18
In the file /etc/vnc.conf
set the line:

$fontPath = "/usr/share/X11/fonts/misc/"

That should do it. At least I got my install of Breezy to pop up with a console.

---


---
title: "xserver-xorg *or* GDM/gnome wont save/set the correct video display size"
date: 2005-05-31
forum: General Help
---

### Post by sandyeggoboy on 2005-05-31
Hello,

i ahve been trying for weeks now to get Hoary installed with the default display manager to work correctly. My system is using an integrated intel i810 video chipset,  and an LCD display. The display is SUPPOSED to go to 1024x768, and when i run the "dpkg-reconfigure xserver-xorg", i always tell it to go to that size, but it ALWAYS on;ly goes to 800x600. when i run the "dpkg-reconfigure xserver-xorg" command, then exit it, the server will no longer run at all. 

Does anyone know how to go about the troubleshooting of this problem? What more info do you need from me? Log files?

Thanks,

Deric Stowell

---

### Post by royg1234 on 2005-05-31
get the 855resolution debian package -->   [http://packages.debian.org/unstable/x11/855resolution](http://packages.debian.org/unstable/x11/855resolution)

Install it (sudo dpkg -i 855resolution_0.3-5_i386.deb), for instructions, see
[list]
[*]/usr/share/doc/855resolution/README.Debian
[*]/usr/sharedoc/855resolution/README.txt
[/list] 

Let me know if this works.

---

### Post by sandyeggoboy on 2006-03-29
Sorry this took so long to get back to you .. this issue has been resolved.


Thanks!!1

---


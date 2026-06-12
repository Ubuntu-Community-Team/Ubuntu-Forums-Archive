---
title: "Unable to type &quot; and ' characters"
date: 2007-01-23
forum: General Help
---

### Post by weijie90 on 2007-01-23
Hi,

I installed Edgy server. I have fluxbox running. 

When I press the ' key (next to the enter button) ' is not typed, but when I type it again a symbol that looks like it appears. The same goes for the " key, and the symbol that appears looks like " but does not work the same way (in google searches " is used to search for an exact phrase). 

By the way, my kernel line in grub contains "usb-handoff". Without that line I couldn't do a text-based login (due to a Can't read CTR while initializing i8042. error) on the first boot. Haven't tried removing that line and using gdm (which I also installed.) 

Should I install the desktop kernel instead of using the server version? I'm using the server install to avoid bloat.

Thanks!

---

### Post by SoggyCornflake on 2007-01-23
> **weijie90 said:**
> Hi,

I installed Edgy server. I have fluxbox running. 

When I press the ' key (next to the enter button) ' is not typed, but when I type it again a symbol that looks like it appears. The same goes for the " key, and the symbol that appears looks like " but does not work the same way (in google searches " is used to search for an exact phrase). 
!

Are you using a US-English Keyboard?  This kind of behavior sounds like what happens when you use certian Euro Keyboards.

---

### Post by weijie90 on 2007-01-23
Hi,
The installer detected it as us-intl.
Thanks!

---

### Post by weijie90 on 2007-01-24
Should I run sudo dpkg-reconfigure console-common?

---

### Post by SoggyCornflake on 2007-01-24
> **weijie90 said:**
> Should I run sudo dpkg-reconfigure console-common?

I've never tried to reconfigure, so I'm not sure.

---

### Post by weijie90 on 2007-01-24
I fixed the problem by getting an xmodmap.us file and running sudo xmodmap /path /to/xomodmap.us

Thanks!

---


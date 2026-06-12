---
title: "which driver is being used in xorg, hardy"
date: 2008-04-22
forum: General Help
---

### Post by Kobin on 2008-04-22
I have installed the hardy-rc and are looking for a way to see which graphics driver is being used. xorg.conf does not show me this anymore and dpkg-reconfigure xserver-xorg skips that part.

Are there a new tool for this, or how can I find out and change it if I want?

---

### Post by Kobin on 2008-04-22
Funny.. After looking for an answer to this problem I found a tool that was already installed even though no present in the menus as far as I can see.

displayconfig-gtk

But when I try to choose Intel 965 and press the test button it fails.
It says my graphics card is (VESA driver(generic)) even when I try to choose the driver for my card.

My problem is that glxinfo gives me:
direct rendering: yes

but I have no 3d acceleration.
By the way cedega tells me the driver used is:
1.4 Mesa 7.0.3-rc2

Any Ideas?

---

### Post by Kobin on 2008-04-22
I have read that it might be a problem with the mesa package:
[http://sudan.ubuntuforums.com/showthread.php?t=731760]("http://sudan.ubuntuforums.com/showthread.php?t=731760")

But where can I download old packages? I have googled a bit on this but not found anything yet...

---


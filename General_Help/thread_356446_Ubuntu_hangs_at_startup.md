---
title: "Ubuntu hangs at startup"
date: 2007-02-08
forum: General Help
---

### Post by stephantom on 2007-02-08
Hello fellow Ubuntuers,

I am running Edgy with the latest generic kernel (2.6.17-10-generic). At bootup, I am seeing a bunch of error messages (see [lines 147-153](http://www.ubuntuusers.de/paste/7369/#code-l147) in the dmesg output), then the bootscreen appears. The progressbar fill up to about half of it. Now it freezes for over a minute. After that, the bar fills up to 100% within a second and GDM greets me.
Does anyone have a clue what happens here?
I can say that it is not because of fsck checking my filesystem (because the bootscreen disappears for this). I have installed the nVidia graphics drivers (as part of my testing with the Beryl window manager).

This is a HP Pavilion dv5000 laptop computer. I am using the internal wireless chipset for networking and I get my settings via DHCP.

For reference:
dmesg: [http://www.ubuntuusers.de/paste/7369/](http://www.ubuntuusers.de/paste/7369/)
lspci: [http://www.ubuntuusers.de/paste/7370/](http://www.ubuntuusers.de/paste/7370/)

Thank you in advance,
stephantom

---


---
title: "Remmina Remote Desktop does not refresh/update image (one way)"
date: 2014-04-06
forum: General Help
---

### Post by I.Bun.Tu on 2014-04-06
I have the exact same problem discussed here:

[http://ubuntuforums.org/showthread.php?t=1879149](http://ubuntuforums.org/showthread.php?t=1879149)

and also here: [http://askubuntu.com/questions/14484/remote-desktop-viewer-doesnt-update-the-image?s=804a0c89-56a0-4c9c-a952-10e250511997#new-answer](http://askubuntu.com/questions/14484/remote-desktop-viewer-doesnt-update-the-image?s=804a0c89-56a0-4c9c-a952-10e250511997#new-answer)

I have a laptop (rogue - 192.168.1.63) connecting to a desktop (peacefactory - 192.168.1.55) for which I just setup my DHCP reservations today.

When I use Remmina on peacefactory to connect to rogue, everything works great from both ends.

When I use Remmina on rogue to connect to peacefactory, the connection works great and I am able to give input from rogue, which is updated on peacefactory. The image in Remmina displayed on rogue however does not update.

This is a one way problem exactly as described by the last poster in the forum thread, but I gather the solution was proposed pre-unity as it refers to changing a gnome setting that is no longer available. I tried gconf-editor but there is only a very small ammount of settings to change and no option to disable_xdamage

Can anyone please tell me how to solve this issue in the current Ubuntu 13.10 version? Thanks.

---

### Post by I.Bun.Tu on 2014-04-09
Is there any more information I can provide? Please let me know, thank you.

---

### Post by I.Bun.Tu on 2014-04-14
Bump

---

### Post by I.Bun.Tu on 2014-04-15
Seriously? What am I doing wrong here? I didn't see any kind of support from Remmina's website over at sourceforge. Is there somewhere else I need to go to get support?

---

### Post by I.Bun.Tu on 2014-04-19
Am I just bumping at the wrong time or does no one know anything about Remmina?

---

### Post by I.Bun.Tu on 2014-04-26
This issue along with a bunch of others was caused by a controller (at least iommu) issue with the AMD 970 chipset on the north bridge of certain motherboards, most notably gigabyte models. I have upgraded to a motherboard with an AMD 990FX chipset and it has solved all of my issues.

---


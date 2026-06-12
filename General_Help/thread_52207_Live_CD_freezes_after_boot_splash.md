---
title: "Live CD freezes after boot splash"
date: 2005-07-26
forum: General Help
---

### Post by nwjsmith on 2005-07-26
When I load the ubuntu 5.04 live CD everything boots great until the ubuntu splash screen, at whose appearance my computer locks up. This also happens when loading the kubuntu live CD.

I have an ati express x200 integrated graphics card, which I can only assume is the source of the problem. I'm also running an AMD Athlon 64 3200+.

Thanks for any help.

---

### Post by Shiven on 2005-07-27
i only have bad news... my amd64 friends have exactly the same problem with any livecd they come across, if they are using a PCI-X card. i don't know of a solution, but it might give you a bit of a focus ^-^

---

### Post by Xiata on 2005-08-29
Likely ATI device framebuffer issue.
Use this as the boot parameter from the cd: linux framebuffer/debian-installer=false (or might be debian-installer/framebuffer=false)

You aren't really frozen, it's just completely unable to show anything on your screen.

(I use an ATI Mobility Radeon 9700)

---


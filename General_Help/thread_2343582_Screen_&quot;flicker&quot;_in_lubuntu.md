---
title: "Screen &quot;flicker&quot; in lubuntu"
date: 2016-11-17
forum: General Help
---

### Post by truerror on 2016-11-17
Well, actually, I'm not sure if "flicker" is the right word for it. It seems to me that the active window's size changes very rapidly. I recently moved from Mint to Lubuntu 16.04 (this is an old Acer netbook, and I figured Lubuntu would've been a better fit since it's lighter), and I've had the same problem in Mint. At this point, I don't know if it's hardware or software. The timing seems pretty random too. Has anyone else encountered this problem?

The netbook has Intel Atom in it. I'm not sure which Intel GPU it has. Probably GMA500.

---

### Post by courtney2 on 2016-11-17
I would try out a different linux distro (like Fedora) and see if the problem still persists. If it does, I would assume it to be a hardware issue. My guess is you used linux distros with the same kernel, and perhaps trying a different kernel/xorg version will tell if it's hardware or software.

---

### Post by truerror on 2016-11-17
Thanks for the reply. Do you think that I can maybe just update the kernel and keep the rest? I mean, as far as window systems go, my old Mint used Cinnamon and lubuntu is LXDE.

---

### Post by oldos2er on 2016-11-17
> **truerror said:**
>  I'm not sure which Intel GPU it has.

Please post the output of ```
lspci | grep VGA
```

---


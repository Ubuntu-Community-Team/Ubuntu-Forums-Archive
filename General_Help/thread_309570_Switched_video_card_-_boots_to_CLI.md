---
title: "Switched video card - boots to CLI"
date: 2006-11-29
forum: General Help
---

### Post by TurkVU on 2006-11-29
Hey - I just switched out my video card from a ATI to a nvidia geforce 6600. After the switch when I boot everything looks fine, but when the Kubuntu 6.10 load screen disappears it brings me to a command line login screen instead of the normal GUI one. How do I get back to the GUI? Do I need to install drivers or change my xorg.conf file from the CLI? If so how do I? I'm still somewhat new to this.

Thanks!!

---

### Post by TurkVU on 2006-11-29
Reconfigured X to use nv instead of flgrx w/

```
sudo dpkg-reconfigure xserver-xorg
```

And now it boots fine.

---


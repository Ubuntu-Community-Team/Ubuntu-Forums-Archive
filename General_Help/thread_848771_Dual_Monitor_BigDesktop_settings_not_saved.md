---
title: "Dual Monitor BigDesktop settings not saved"
date: 2008-07-03
forum: General Help
---

### Post by pulse00 on 2008-07-03
Hi all,

i've switched from fedora to ubuntu and i have to say i'm really impressed, never had a full compiz enabled desktop running without any pain like with this distro.

The only thing what's bugging me is that i can't get my dual monitor setup work in BigDesktop mode. When using the ATI Control Center, i can set it to BigDesktop. After doing so, X Server switches into this mode, and also alters xorg.conf. 

However, after restaring the computer, the monitors work in clone mode again... I have no idea what the ATI Tool does when switching, but it alters the xorg.conf and at least adds a line

```
Options "DesktopSetup" "Horizontal"
```

to the DeviceSection.

Anyone knows how i could make this persistent ?

---


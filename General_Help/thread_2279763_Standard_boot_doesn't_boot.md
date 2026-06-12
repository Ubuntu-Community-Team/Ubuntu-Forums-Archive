---
title: "Standard boot doesn't boot"
date: 2015-05-25
forum: General Help
---

### Post by michaelpulliam1 on 2015-05-25
Well actually it sort of boots. I'm having an issue to where if I select Ubuntu in the grub menu X doesn't load (And nothing works from Ctrl + Alt + Backspace to Ctrl + Alt + Del. I have to use my case's restart button), but if I select the```
 Ubuntu with linux kernel [whatever the version is] (upstart) 
```it loads.
I've changed some things (installed cinnamon and changed grub.cfg in attempt to get my back USB 3.0 ports working) and I think that's the only thing that would break things though I'm not certain.
I looked at the 15.04 thread describing that you use Systemd (It might have something to do with it) now, but Ubuntu loaded properly on the first boot.
If there's any information I might be able to provide (logs, lshw and the like) just say so.

Edit: Not grub.cfg; /etc/default/grub

---

### Post by michaelpulliam1 on 2015-05-26
If nobody knows of a solution could you please instruct me on how to make the upstart boot thingy default?

---

### Post by v3.xx on 2015-05-26
An easy fix would be to install 14.04.  It defaults to 'upstart' and unlike 15.04, it will be supported for 5 years.  14.04 is a LTS release.

---

### Post by michaelpulliam1 on 2015-05-26
Thank you @v3.xx, You helped me to see the problem from a different angle.
My fix is more of a workaround that an fix.
I edited /etc/default/grub from
```
GRUB_DEFAULT=0
```
to
```
GRUB_DEFAULT="1>1"
```

What that does is sets the default in the grub menu to the first submenu, first option; that just so happens to be the (upstart) selection. You see, I didn't know that you could select anything in a submenu for booting!

If a fix is found, I would like it pm'd to me. Though I will mark this as solved.

Thanks again!

---


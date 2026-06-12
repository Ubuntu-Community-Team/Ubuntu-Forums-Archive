---
title: "setting up new videocard"
date: 2007-12-29
forum: General Help
---

### Post by nonewmsgs on 2007-12-29
i got a nvidia tnt videocard for dad's p3 1ghz ubuntu machine.  once x starts the screen goes blank, er rather did until i started running the dpkg-reconfigure xserver-xorg

lspci has said that i have  a vga compabale controller nvidia nv6 [vanta/vanta lt] (rev 15) at 01:0e.0

i tried to punch that in as pci:01:0e:0 in the wizard, but it says that is not a valid entry.
pci:01:0:0 does not work :(

any ideas?

current error message
fatal server error:
no screens found

---

### Post by ~LoKe on 2007-12-29
Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nonewmsgs on 2007-12-29
still nothing.  i have tried vesa and vga as well as nv

(ww)vesa no matching device section for instance (busid pci:1:14:0) found
(ee) vesa(0) cannot read v_bios(3)
(ee)screen(s) found, but none have a usable configuration

also it compains about not having a battery but it's not a laptop.

---


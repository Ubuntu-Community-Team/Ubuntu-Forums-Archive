---
title: "Dual boot Ubuntu and Mandriva"
date: 2006-12-01
forum: General Help
---

### Post by Roberto Rosselli on 2006-12-01
Hi all,
I'm trying to dual boot my box with Ubuntu and Mandriva using LILO, but so far with little success. This is my lilo.conf:

```
default="linux"
boot=/dev/hda
map=/boot/map
keytable=/boot/it-latin1.klt
menu-scheme=wb:bw:wb:bw
compact
prompt
nowarn
timeout=100
message=/boot/message
image=/boot/vmlinuz
        label="linux"
        root=/dev/hdb3
        initrd=/boot/initrd.img
        append=" resume=/dev/hda5 splash=silent"
        vga=788
image=/boot/vmlinuz
        label="linux-nonfb"
        root=/dev/hdb3
        initrd=/boot/initrd.img
        append=" resume=/dev/hda5"
image=/boot/vmlinuz
        label="failsafe"
        root=/dev/hdb3
        initrd=/boot/initrd.img
        append=" failsafe resume=/dev/hda5"
image=/boot/vmlinuz-2.6.15-27-686
        label="Ubuntu_2.6.15-27_686"
        root=/dev/hdb2
        initrd=/boot/initrd.img-2.6.15-27-686
image=/boot/vmlinuz-2.6.15-27-386
        label="Ubuntu_2.6.15-27_386"
        root=/dev/hdb2
        initrd=/boot/initrd.img-2.6.15-27-386
image=/boot/vmlinuz-2.6.15-26-686
        label="Ubuntu_2.6.15-26_686"
        root=/dev/hdb2
        initrd=/boot/initrd.img-2.6.15-26-686
image=/boot/vmlinuz-2.6.15-26-386
        label="Ubuntu_2.6.15-26_386"
        root=/dev/hdb2
        initrd=/boot/initrd.img-2.6.15-26-386
other=/dev/hda1
        label="windows"
        table=/dev/hda
```

At the present moment Ubuntu fails to boot properly and I'm returned to a root prompt, I suspect that's because the system.map and/or config files point to the Mandriva ones.

How can I modify my lilo.conf to have Ubuntu boot fine? Any help greatly appreciated, thank you!

RR

---


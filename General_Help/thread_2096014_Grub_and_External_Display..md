---
title: "Grub and External Display."
date: 2012-12-18
forum: General Help
---

### Post by p2bc on 2012-12-18
Long story short. I have a MacBookPro about a year old with busted display. Manage to get to the Grub menu off of a UBS Live ISO of Ubuntu 12.10 using an external display. The moment the bios hands off control to the OS the external display goes blank. After a few seconds I do hear the typical Ubuntu initial sound, just can see anything. I found a few post saying use "xrandr --output LVDS --same-as VGA..." anyways, I get an error saying " Could not find 'xrandr'". Unless I am mistake as to how to use the xrandr command is there a way to edit the grub entry to tell it to continue to use the external display after it hands off to the OS? If so could someone be so kind as to show me the errors of my ways.

The code as it is right now:
```

setparams 'Install Ubuntu'

                   set gfxpayload=keep
                   linux        /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubuquity quiet splash --
                   initrd       /casper/initrd.lz

```Thanks so much.

---

### Post by dcstar on 2012-12-19
> **p2bc said:**
> Long story short. I have a MacBookPro about a year old with busted display. Manage to get to the Grub menu off of a UBS Live ISO of Ubuntu 12.10 using an external display. The moment the bios hands off control to the OS the external display goes blank. After a few seconds I do hear the typical Ubuntu initial sound, just can see anything. I found a few post saying use "xrandr --output LVDS --same-as VGA..." anyways, I get an error saying " Could not find 'xrandr'"

[http://linux-tipps.blogspot.com.au/2009/03/automatically-switch-to-connected.html](http://linux-tipps.blogspot.com.au/2009/03/automatically-switch-to-connected.html)

---

### Post by p2bc on 2012-12-20
I did see that that page while I was researching the problem but did not give it much thought because I am working with ISO image, but after a second read with the persistent  drive I will be able to create the script on another machine and then return to the broken one.

---


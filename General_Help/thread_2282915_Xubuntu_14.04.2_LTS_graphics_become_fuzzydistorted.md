---
title: "Xubuntu 14.04.2 LTS graphics become fuzzy/distorted after a while...please help!"
date: 2015-06-17
forum: General Help
---

### Post by alex405 on 2015-06-17
Hi, I am running Xubuntu on an older laptop (6 years old) and everything runs fine but the graphics become "glitchy" after the computer has been running for a few hours.

The desktop background becomes distorted but it fixes itself if I switch to a new workspace and go back to the original. I've experienced the same thing on several programs such as the browser and the PDF viewer. Tabbing out fixes this issue. This does not affect my computer's performance in any way but it gets really annoying. Any help would be greatly appreciated.   

I'm running 14.04.2 LTS Xubuntu with the 3.16.0-41-generic kernel if that helps.

BEFORE:

[ATTACH=CONFIG]262668[/ATTACH]


AFTER:

[ATTACH=CONFIG]262669[/ATTACH]

---

### Post by QIII on 2015-06-17
Hello!

Please do not paste large images.  Some users have slow connections or bandwidth limitations.

To insert an image, please use the attachment functionality by clicking the "paper clip" button above the text input box.

Thanks.

---

### Post by alex405 on 2015-06-17
Thanks for the tip. Will keep this in mind in future threads.

---

### Post by ajgreeny on 2015-06-17
What graphic card and driver are you using?

---

### Post by alex405 on 2015-06-17
> **ajgreeny said:**
> What graphic card and driver are you using?
I believe it's a generic Intel integrated graphics card.
I hope this helps:

```
sudo lshw -c video  
*-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff



```

---

### Post by alex405 on 2015-06-18
any help?

---

### Post by alex405 on 2015-06-18
hi.

---

### Post by ajgreeny on 2015-06-18
This might be a wild goose chase, but I wonder if 14.04.1 might have better graphics for you than 14.04.2 which has a later version of xorg, and a later kernel version, having been upgraded to the utopic 14.10 hardware stack.

I don't know if this would help, and unfortunately I do not know if you can easily downgrade the related packages to try it, but you could at least try a live system of 14.04.1 to see if the graphics glitch still appears.  If that version runs OK you can consider reinstalling the OS, but wait until others have answered, as I may be wrong about the downgrading of the hardware stack.

---

### Post by alex405 on 2015-06-20
> **ajgreeny said:**
> This might be a wild goose chase, but I wonder if 14.04.1 might have better graphics for you than 14.04.2 which has a later version of xorg, and a later kernel version, having been upgraded to the utopic 14.10 hardware stack.

I don't know if this would help, and unfortunately I do not know if you can easily downgrade the related packages to try it, but you could at least try a live system of 14.04.1 to see if the graphics glitch still appears.  If that version runs OK you can consider reinstalling the OS, but wait until others have answered, as I may be wrong about the downgrading of the hardware stack.

thanks, hopefully someone can give their input on this.

---

### Post by alex405 on 2015-06-24
nobody got a clue?

---

### Post by alex405 on 2015-07-10
up

---

### Post by alex405 on 2015-07-11
up

---


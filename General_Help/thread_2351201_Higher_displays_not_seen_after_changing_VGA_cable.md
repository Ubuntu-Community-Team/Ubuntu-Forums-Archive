---
title: "Higher displays not seen after changing VGA cable"
date: 2017-02-01
forum: General Help
---

### Post by Milind on 2017-02-01
My PC is an Ubuntu 16.10/Win 10 dual boot machine.

Processor:Intel® Core™2 Duo CPU E7400 @ 2.80GHz × 2 
Graphics: Intel® G33 
2GB Ram

A few days ago the display started turning weird shades of green, though I could still use the computer. The VGA cable seemed to be loose & at fault, so I changed it. After changing, though the colours were back to normal, in both Ubuntu & Windows 10 the maximum resolution shown was 1024*768 @60 Hz, though the Dell LCD monitor's maximum is 1600*900 @60 Hz. In Windows, I could find the higher settings in Advanced Display Settings and get things back to normal. But Ubuntu Settings do not show any resolutions except 800*600, & 1024*768. How can I get the higher resolutions back?

Thanks in advance for any help.

---

### Post by DuckHook on 2017-02-01
It would be too coincidental for something else to have borked your resolution at the exact time as you changed your cable. Therefore, I would strongly suspect the cable.

Check to see that all pins are present. Some VGA cables have missing pins for historical reasons that are too pedantic to get into right now. Some cheap Made In China ones even have the pins but are missing the internal wires! These missing connections will prevent the monitor's EDID from being read by your GPU. Windows has different ways to guess at EDID. Ubuntu can force an EDID too, but it is very arcane. Better to just change cables again to one that is complete. With modern video, it is a good idea generally to invest in quality cables and not go for the cheap ones. Also, make sure you are not connecting via KVM switch. It doesn't sound like you are, but they are real culprits for blocking EDID signals.

---

### Post by Milind on 2017-02-01
All the pins were present. I tried changing back to the old cable. The higher displays returned (as did the weird colouring). So, you're probably right, the new cable is the problem for Ubuntu. However, as the colour given by the old cable is terrible, for the time being, till I get another, and better, cable, I have reverted to the new cable and am using Windows 10. Meanwhile, if anyone can suggest a software solution.....

---

### Post by DuckHook on 2017-02-01
> **Milind said:**
> Meanwhile, if anyone can suggest a software solution.....
The following link will take you to an old but still relevant thread: [https://ubuntuforums.org/showthread.php?t=2193634&p=12873807#post12873807](https://ubuntuforums.org/showthread.php?t=2193634&p=12873807#post12873807)

Do not implement the later solutions in that thread. Since writing it, I've come to conclude that it is easier to change your .xprofile than it is to create and fiddle with an xorg.conf file, but the thread should at least give you an idea of what your requested software solution involves.

If you still want to go that way, then give a shout. Otherwise, it may be simpler to just wait for that cable. BTW, make sure you buy it from someone who will accept returns in case it doesn't work either.

---


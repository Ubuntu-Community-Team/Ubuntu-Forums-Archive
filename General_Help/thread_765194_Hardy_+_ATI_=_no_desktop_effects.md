---
title: "Hardy + ATI = no desktop effects"
date: 2008-04-24
forum: General Help
---

### Post by orbital on 2008-04-24
Never mind.

---

### Post by Homesickblues on 2008-04-24
I'm having the same problem how did you solve it?:(

---

### Post by Ub1476 on 2008-04-24
Additional drivers can be downloaded from System->Administration->Hardware Drivers.

---

### Post by AndyC_772 on 2008-04-26
The only one I have listed is the one for my wireless card - there's nothing in there about video drivers.

My /etc/X11/xorg.conf lists my display driver as "ati" - presumably correct? Yet when I try to enable desktop visual effects I just get an error box "Desktop effects could not be enabled", with no clue given as to why.

They worked fine in Gutsy - just tried updating and now it's broken :(

---

### Post by hodenkat on 2008-04-26
I got the desktop effects to work, but now when they are enabled I get video corruption. Stuff like vertical lines and hash marks on the screen. Also the effects are really slow. Very strange since they worked flawlessly in 7.10!
This was after trying

sudo aptitude install xserver-xgl
sudo aptitude install compizconfig-settings-manager

Before doing the above, desktop effects would not even enable.

---

### Post by shottie on 2008-04-26
> **hodenkat said:**
> I got the desktop effects to work, but now when they are enabled I get video corruption. Stuff like vertical lines and hash marks on the screen. Also the effects are really slow. Very strange since they worked flawlessly in 7.10!
This was after trying

sudo aptitude install xserver-xgl
sudo aptitude install compizconfig-settings-manager

Before doing the above, desktop effects would not even enable.

I had the same problem, i had to switch driver to the vesa (from the ati driver using "sudo displayconfig-gtk" at the terminal), then i had to manually edit the xorg.conf to set up my resolution.  Hope this helps!

---

### Post by hodenkat on 2008-04-26
> **shottie said:**
> I had the same problem, i had to switch driver to the vesa (from the ati driver using "sudo displayconfig-gtk" at the terminal), then i had to manually edit the xorg.conf to set up my resolution.  Hope this helps!

No difference. I didn't have to edit the resolution but I did check it and it was correct. wonder why they didn't keep the driver from 7.10?
It worked fine.#-o

---

### Post by sh0N on 2008-04-26
> **hodenkat said:**
>  wonder why they didn't keep the driver from 7.10?
It worked fine.#-o


AMEN!!

---

### Post by Rocket2DMn on 2008-04-26
The open source "ati" drivers are blacklisted for Compiz Fusion because of a bug in the driver, but they can be easily made to work.  Here is a quick guide to get it working - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by shottie on 2008-05-16
> **hodenkat said:**
> No difference. I didn't have to edit the resolution but I did check it and it was correct. wonder why they didn't keep the driver from 7.10?
It worked fine.#-o

Yep it did, xwinwrap really slows down my system now but in gutsy if was perfect!

---


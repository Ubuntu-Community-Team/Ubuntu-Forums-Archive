---
title: "Dual Monitors"
date: 2006-07-02
forum: General Help
---

### Post by JoshHendo on 2006-07-02
Ok, so today I put another monitor on this computer. It has a ATI Radion (I think thats how you spell it). So, I plugged the other screen in (to the other port on the card, as it is a dual card), and booted up Ubuntu.

It was able to make it a clone, so it was the same on both screens, but I can't work out how to make it so that it has one long desktop extending through both.

I booted up the kubuntu live cd (as I heard kde is better at supporting dual monitors), but I couldn't change the settings in Display to how I want it.

I tried installing the ATI drivers on kubuntu, but I haven't yet tried in Ubuntu.

Would someone be able to link me to a article that would help me set this up in Ubuntu. If it is only possible in Kubuntu, I would be happy to install that.

Thanks :)

---

### Post by scxtt on 2006-07-02
check out these 2 commands:
[indent]aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
/etc/init.d/gdm restart[/indent]and if that doesn't work, you might need to get ati (fglrx) drivers installed - see my sig for that ... i'm using dual on an ATI as we speak (patiently waiting for my new [2nd] 20.1" LCD monitor to replace this 17" CRT) :D ...

---


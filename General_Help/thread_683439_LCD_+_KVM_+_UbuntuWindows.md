---
title: "LCD + KVM + Ubuntu/Windows"
date: 2008-01-31
forum: General Help
---

### Post by RandomZero on 2008-01-31
So I have two different pc's connected with one KVM and I use an LCD monitor.

I used to have Ubuntu on one and Vista on another, but there was this odd issue where the screen would be slightly to the left on Ubuntu, but if I corrected it, the same thing would happen to Vista.
The Ubuntu pc has an nvidia vid card, the Vista has ATI.
My solution to this was to switch the Ubuntu pc to Server2003.

But, my friend just went out and got a widescreen LCD, and he's using a kvm switch with Ubuntu on one pc and XP on another. And he has the same issue now.
LCD's aren't the same brand or even size, KVM's aren't the same brand, Vid card's aren't the same (Although he does have one nvidia and one ATI).

Anyone know of a way to fix this?

Keep in mind that NONE of the equipment is the same model, most aren't even the same brand. The ONLY similarities are ATI/Nvidia and Ubuntu/Windows.

---

### Post by Shazaam on 2008-01-31
One functionality that I miss from Windows is the gui setup for screen position.
That said try this= boot the Ubuntu pc first and use the monitor OSD (On Screen Display) to position the screen. Switch to the Windows box and use the ATI Control center (or the nvidia settings depending on the card) and set it's screen position.

---

### Post by confused57 on 2008-01-31
> **RandomZero said:**
> So I have two different pc's connected with one KVM and I use an LCD monitor.

I used to have Ubuntu on one and Vista on another, but there was this odd issue where the screen would be slightly to the left on Ubuntu, but if I corrected it, the same thing would happen to Vista.
The Ubuntu pc has an nvidia vid card, the Vista has ATI.
My solution to this was to switch the Ubuntu pc to Server2003.

But, my friend just went out and got a widescreen LCD, and he's using a kvm switch with Ubuntu on one pc and XP on another. And he has the same issue now.
LCD's aren't the same brand or even size, KVM's aren't the same brand, Vid card's aren't the same (Although he does have one nvidia and one ATI).

Anyone know of a way to fix this?

Keep in mind that NONE of the equipment is the same model, most aren't even the same brand. The ONLY similarities are ATI/Nvidia and Ubuntu/Windows.
I hope someone has a solution for this problem.  I have a pc with Ubuntu on one hard drive and XP on the other...the screen is offset to the left if I boot from XP to Ubuntu or vice-versa.  I have to press the "Auto" reset button on the LCD each time I boot into the other OS.

---

### Post by Shazaam on 2008-01-31
confused57......
Try what I posted and see if it works.

---

### Post by confused57 on 2008-01-31
> **Shazaam said:**
> confused57......
Try what I posted and see if it works.
Thanks Shazaam, that seems to work when booting from Ubuntu back into Windows...I used to have to use the "Auto" tune button on the LCD to get Windows desktop centered(it was approx. 1/2 inch set to the left before moving the screen position in Nvidia settings).  When I boot back into Ubuntu the login screen is set about 1/2 page to the left, but the Auto tune feature on my LCD automatically repositions the screen correctly(which it was doing before making the change).  
Thanks again, at least I don't have to manually reposition the Windows desktop.

---


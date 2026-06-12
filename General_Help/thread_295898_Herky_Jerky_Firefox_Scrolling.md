---
title: "Herky Jerky Firefox Scrolling"
date: 2006-11-08
forum: General Help
---

### Post by sadalmelik57 on 2006-11-08
I'm really annoyed by the way scrolling down or up occurs in Firefox 2.0 after the upgrade to Edgy Eft.  I'm not certain if this is a result of the mouse configuration (IfeelMouseMan 3-button with scroll wheel) or if this is something about the new Firefox 2.0.

No matter what method I use to scroll up or down, I see a jerky line-by-line movement of the page up or down.  It is slow and looks terrible.  I tried Mozilla Web Browser and the effect seemed to be greatly reduced but still evident.

I've tried to adjust the mouse using the user preferences in Ubuntu, and I've changed the Advanced Preferences in Firefox for smooth scrolling and autoscrolling.  None of these had any affect.  What else can I do to change the scrolling to make it smooth and faster?

---

### Post by IusedTObeSOMEONEelse on 2006-11-08
I thought maybe it was just me but I seem to have the same behavior. Scrolling up/down is jumpy and Firefox 2 seems so slooow!! :-k

---

### Post by SirShaggy on 2006-11-08
YES, Me too! I am all annoyed about it. I just got here looking for answers....
SirShaggy

---

### Post by fragos on 2006-11-09
Try Firefox Preferences-> Advanced-> "Use smooth scrolling" check box

---

### Post by sadalmelik57 on 2006-11-09
I tried the "smooth scrolling" (both on and off) in Firefox 2.0 "Preferences - Advanced - General" tab and there was no difference.

(Thanks, George - and all other Vets!)

---

### Post by rado on 2006-11-19
I tried another browsers scrolling was the same. I think that problem is inside OS. Draging an open window on the desktop has the same movement.
Draging "big" pictures in the image viewer as well.

---

### Post by rado on 2006-11-20
I've just done it! Problem is that we need switch off composite extentions in grafic card. System - Software source - Software restricted " turn on"

Into terminal write: uname -r   to know your kernel version
than: 
sudo apt-get update
sudo apt-get install linux-restricted-modules-(behind last dash write number of your kernel version)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

than restart in terminal with:
sudo shutdown -r now

---

### Post by DougieFresh4U on 2006-11-20
I switched to Swiftfox Browser and it cured all problems and much faster.

---

### Post by PrinceArithon on 2006-11-20
You should also check your xorg file to see if everything is at it's peak performance.

---

### Post by Smurfy on 2006-11-26
Hi,I've just joined the forum and am completely new to (K)ubuntu.
I don't know anything about using terminals as yet but I had this jerky scrolling problem and nearly went back to Windows because of it.However I managed to solve it quite easily.I did'nt have this option in Ubuntu but in Kubuntu I used system settings/monitor/hardware/configure and Kubuntu automatically found my graphics driver (Geforce)and installed that instead of Mesa.Reboot and problem solved.;)

---

### Post by Melk79 on 2008-04-17
Old thread, but...

From other posts, I found changing the display from 24-bit to 16-bit in the xconf.org file fixed this problem.  Smooth scrolling now and the desktop image is improved.

---

### Post by forrestcupp on 2008-04-17
Also, if you happen to be using Compiz with an ATI video card, installing the latest drivers with Envy takes care of that problem, too.

---

### Post by BLTicklemonster on 2008-04-17
I did that once, and it totally messed up the game I play, and had other effects that were not wanted. And changing it back to 24 bit didn't work at all. I had to go to vesa driver, reboot, go back to nvidia restricted drivers, then reboot again.

---


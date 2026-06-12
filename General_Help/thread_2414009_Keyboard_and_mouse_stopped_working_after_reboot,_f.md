---
title: "Keyboard and mouse stopped working after reboot, following update"
date: 2019-03-04
forum: General Help
---

### Post by horseatingweeds2 on 2019-03-04
I let Ubuntu 16.4 do updates, then restarted, and my laptop keyboard and mouse stopped working. I tried rebooting again, using the touch screen. Still didn't work. I plugged in a keyboard and mouse, which both worked. I read about others having the issue. They reinstalled xserver like so:

sudo apt-get install xserver-xorg-input-all

But my system complained of broken packages. So I found another bit of advice to install it like this: sudo apt-get install xserver-xorg-core

I rebooted and now no input device works -- not the touch screen, mouse pad, USB mouse, or keyboard. 

I booted into recovery mode and got a root terminal, after enabling networking. I tried running 

sudo apt-get install --reinstall xserver-xorg

but that complains that it "temporarily failed to resolve us.archive.ubuntu.com" which I take to mean it's actually not able to reach the network, confirmed by trying to ping anything. Same if I try apt-get update. 

What do I do now???

---

### Post by horseatingweeds2 on 2019-03-05
I sorted it out, finally, I think. Once I got home networking in recovery mode worked and I was able to final successfully run 

sudo apt-get install --reinstall xserver-xorg

which seems to have fixed the issue.

Prior to that, I also ran this: 

apt-get remove --purge nvidia-*

But the terminal just got stuck. I had to to a hard reset to get out. I went back into recovery reinstalled xserver.

---


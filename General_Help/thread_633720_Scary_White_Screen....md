---
title: "Scary White Screen..."
date: 2007-12-06
forum: General Help
---

### Post by B-randon on 2007-12-06
Ok, I've used Ubuntu before on this same computer a while back. I recently switched from ATI video card to a Nvidia (if that would make much of a difference.) Also i may add that I am dual booting ubuntu with windows xp

So, i went to start ubuntu and it said something was missing. I got the latest version of wubi and re-installed ubuntu. It starts fine but right after i log in my screen goes white. I can move my mouse and when i click on the bottom right hand corner it looks like its opening windows, BUT it just stays there and thats all that i can do. Through pressing alt+s i can get it to close and shutdown my system. 

What's wrong here and is there anyway to fix it? :confused:


Help is very much appreciated.


Thanks :)

---

### Post by -grubby on 2007-12-06
you can reboot into recovery mode. Then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and select the correct video driver

---


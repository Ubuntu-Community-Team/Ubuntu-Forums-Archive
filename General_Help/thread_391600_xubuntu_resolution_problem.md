---
title: "xubuntu resolution problem"
date: 2007-03-23
forum: General Help
---

### Post by anv on 2007-03-23
My question lies in xubuntu environment, we installed xubuntu on my friends box, and now everything seesms to work fine but under display menu, there reads just default,nothing more, seems to be something 640x480 or 800x600 so resolution is quite low. how we could set it little higher, it is server machine with inbuilt cirrus something graphic adapter.

---

### Post by john.nicholls on 2007-03-23
In a terminal type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by motoperpetuo on 2007-12-28
i got a new samsung syncmaster 226bw 22" flat-panel monitor for xmas and i'm trying to get it to work on an old sony vaio with a nVIDIA® GeForce2 / TNT2-Model64 Graphics Adapter. It works beautifully on this machine under Windows XP. i get 1680x1050 resolution and crystal-clear, crisp colors.

before running the above suggested command and running through the xserver reconfiguration utility, i was getting 1024x800 resolution (or something like that). now i'm only offered 1920x1200 (which doesn't work) and 800x600 and 640x480.

is there any hope for me? if the video card and monitor work like a champ under windows, there should be some way to get them to work in xubuntu, shouldn't there? would i be better off adding a little RAM to this machine and trying in ubuntu or some other distro like pclinuxos or opensuse?

---

### Post by motoperpetuo on 2007-12-31
> **motoperpetuo said:**
> i got a new samsung syncmaster 226bw 22" flat-panel monitor for xmas and i'm trying to get it to work on an old sony vaio with a nVIDIA® GeForce2 / TNT2-Model64 Graphics Adapter. It works beautifully on this machine under Windows XP. i get 1680x1050 resolution and crystal-clear, crisp colors.

before running the above suggested command and running through the xserver reconfiguration utility, i was getting 1024x800 resolution (or something like that). now i'm only offered 1920x1200 (which doesn't work) and 800x600 and 640x480.

is there any hope for me? if the video card and monitor work like a champ under windows, there should be some way to get them to work in xubuntu, shouldn't there? would i be better off adding a little RAM to this machine and trying in ubuntu or some other distro like pclinuxos or opensuse?

note: i got this working a few days ago. i ran the utility that john.nicholls suggested above, then i downloaded the nvidia drivers through synaptic. there was one snag, in that i originally download the nvidia-legacy package, which didn't work, even though it said it was for geforce2 cards. after that, i tried the nvidia-new package and it worked fine. i'm guessing it was a combination of the two that made it work.

---


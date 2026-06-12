---
title: "[SOLVED] Anything 3D works extremly poorly"
date: 2007-08-07
forum: General Help
---

### Post by Aesir09 on 2007-08-07
ok, anything i try to do 3d such as screen savers, games(nexuiz) is just really choopy and impossible.

and also when running tests in cedega it said something wrong about 3d matter,

HELP?
i need to game :lolflag:

---

### Post by Songwind on 2007-08-07
What kind of video card are you using?

Which drivers?

---

### Post by Aesir09 on 2007-08-07
its an nvidia geforce
erm where should i get drivers havent done that yet.
if i go to their website?

---

### Post by Songwind on 2007-08-07
> **Aesir09 said:**
> its an nvidia geforce
erm where should i get drivers havent done that yet.
if i go to their website?

For good 3D performance you need to use the proprietary drivers.  Ubuntu by default uses the open source drivers, which are not yet 3D accelerated.

Installing the new drivers is easy - there is a package.

Install the "nvidia-glx" package from Synaptic, or run
```
sudo apt-get install nvidia-glx
```

There is a nice quick tutorial here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)

---

### Post by Aesir09 on 2007-08-07
thanks alot man :)

---


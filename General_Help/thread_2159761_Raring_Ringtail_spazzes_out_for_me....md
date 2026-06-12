---
title: "Raring Ringtail spazzes out for me..."
date: 2013-07-04
forum: General Help
---

### Post by TheWomanWhoLivesInAShoe on 2013-07-04
I upgraded from Quantal to Raring. But upon opening some of my 3D  applications, like Blender, the screen freezes then a glitch screen  appears. On LXDE, I had success in opening Blender, but only once. I  can't run MMDAI2, because the 3D view becomes unusable, then it freezes the  system. Then at one instance, I couldn't log in due to a freeze. How can I solve this bug? On Debian, I couldn't run MMDAI2 and I had no success in compiling it.

---

### Post by DeathByDenim on 2013-07-04
It kind of sounds like your graphics drivers became broken. Did you try (re)installing the latest from the repositories for whatever graphics card you have?

---

### Post by TheWomanWhoLivesInAShoe on 2013-07-04
But how I should do that? My computer is in Japanese.
I have an nVidia graphics card. What should I install?
NVidia binaries for X.Org or what?

---

### Post by DeathByDenim on 2013-07-04
For nvidia, you can type
```
sudo apt-get install nvidia-current-updates
```
which will install the NVidia drivers for you.

If that one doesn't work for you, you can try a different version by just typing
```
sudo apt-get install nvidia-
```
, but press <Tab> twice instead of <Enter> to get a list. In Ubuntu 12.04 you can choose for nvidia-experimental-304 and nvidia-experimental-310 for example. I think for your Raring, you should be able to get 313 even.

(Language doesn't matter)

---


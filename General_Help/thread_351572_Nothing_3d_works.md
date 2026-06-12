---
title: "Nothing 3d works"
date: 2007-02-02
forum: General Help
---

### Post by NorthernPaladin on 2007-02-02
Thats the problem. All 2d games work, but none of the 3d games. I don`t know what the problem is, I have installed newest drivers with envy script(my graphics card is nvidia geforce4 ti 4200, processor is amd athlon 2600+, 1,9gHz). 3d programs do start, but fps is from 1 to 10, and after a short period they stop totally. I don`t understand much about linux so try to put step by step directions. 

Thank you all in advance

---

### Post by jd65pl on 2007-02-02
Do the following in the terminal, if it returns "direct rendering: Yes" then your drivers are set up properly. If it doesn't then you don't have hardware acceleration and thus no 3D performance.

```
glxinfo | grep 'direct render'
```

---

### Post by laidback on 2007-02-02
See this link:-

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

from what I see your card is suported for 3D, suggest you read the BinaryDriverHowTo link to  check your installation.

I've never installed a 3D card so cannot help beyond the reference.

Good luck.

---

### Post by NorthernPaladin on 2007-02-02
"glxinfo | grep 'direct render' "   returned    "direct rendering: Yes "
so thats ok. I`ll check the guide when I have finished backing up my files
I installed my drivers using the script   "envy" from  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by fragos on 2007-02-03
If the nvidia driver from the Ubuntu repositories is installed with Synaptic very consistent and successfull installs result.  The Ubuntu package is nvidia-glx.  I run Ubuntu on an AMD Sempron 2800+ with an AGP FX5200 card.  My fps are over 1,300 and our configurations aren't that different.  My advice, stick with Ubuntu recommended solutions when available.

---

### Post by laidback on 2007-02-03
fragos,
Would this work with onboard graphics as well?

---


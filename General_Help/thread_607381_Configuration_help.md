---
title: "Configuration help"
date: 2007-11-08
forum: General Help
---

### Post by pipboy88 on 2007-11-08
Sorry to make a new post about this. I'm new to linux and having the oddest problem. I'm using a Radeon 9600, ubuntu was nice enough to automatically install my drivers and all is well. The problem is that Randomly my Advanced desktop effects stop working. I tried to fix them but in the end decided that I must of messed something up and since a fresh install worked I reinstalled. I started to set up advanced desktop effects and yet again I get stonewalled. The error I get is "the composite extension is not available". Some say its a problem with ATI drivers but I find that hard to believe since if it was then I would of got no effects to start with. Any help is appreciated.

---

### Post by Maestro23 on 2007-11-08
Have you enabled the composite option in your xorg.conf file?  Take a look at the following link from the compiz wiki regarding ATI cards.

[http://wiki.compiz-fusion.org/Hardware/ATI](http://wiki.compiz-fusion.org/Hardware/ATI)

---

### Post by pipboy88 on 2007-11-08
Hmm.. That seemed to help. Now I get "Desktop effects cannot be loaded" which sounds a bit better :P Thanks :) 

I will keep reading into it, suggestions always appreciated.

---

### Post by strabes on 2007-11-08
Please paste the output of this command in this forum. To run commands, open a terminal, which you can access at Applications > Accessories > Terminal.```
fglrxinfo
```

---

### Post by pipboy88 on 2007-11-09
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

---


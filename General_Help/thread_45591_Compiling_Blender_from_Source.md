---
title: "Compiling Blender from Source?"
date: 2005-06-30
forum: General Help
---

### Post by Havoc on 2005-06-30
Hello,

Since the new Blender 2.37a came out, I thought I would might as well plunge in and learn how to model.But, I'm having problems with compilation.I know about the Binaries on the Blender website, but the normal one doesn't work well and the static one makes me believe that I'm not using 100% of the power given.So, compiling!

Could someone drive me through compilation (Dependancies, Make, Make install, etc...), since I'm having problems, and documentation is skimpy? Mabye someone could even write a small HOWTO....no?  :-|

---

### Post by Funzo on 2005-06-30
Blender uses OpenGL for the interface and just about everything else. Without knowing what problems you are having I would suggest installing the freeglut-dev package. Search for freeglut on Synaptics. By default Ubuntu comes with freeglut but not the development packages.

Hope this helps.

---

### Post by not_yet on 2005-07-01
compile Blender with scons

scons is avaiable via Synaptic

cheers

---


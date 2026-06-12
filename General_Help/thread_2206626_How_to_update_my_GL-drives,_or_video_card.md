---
title: "How to update my GL-drives, or video card?"
date: 2014-02-19
forum: General Help
---

### Post by duckfeeder105.5 on 2014-02-19
Hello!

My friend just installed Garry's mod for me and when I ran it, it said this: "Could not find required openGL entry point 'glGetError'! Either your video card is unsupported, or your openGL driver needs to be updated"

I am trying to run it on a TOSHIBA laptop, it has ubuntu installed, of course :p

Now, here's the question, which one do I do? Update my GLdrive, or (try to) get a new video card?

EDIT: 
Heres the output from lspci | grep VGA

Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

Heres the output from glxinfo | grep OpenGL after installing mesa-utils

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) IGD x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 9.1.7
OpenGL extensions:

---

### Post by deadflowr on 2014-02-20
If you know what gpu you have, please tell.

If not, then try this
Open a terminal (that's the name of the program) and type this
```
lspci | grep VGA
```
Post the output back here.
This should tell us the card.
It is possible, depending on the card, to install other drivers(maybe better/newer) for it.

---

### Post by monkeybrain20122 on 2014-02-20
open a terminal and type this to install mesa-utils
```
sudo apt-get install mesa-utils
```

Then run
```
glxinfo | grep OpenGL
```
and post the outputs.

---

### Post by duckfeeder105.5 on 2014-02-20
I updated the original post with the outputs

---

### Post by monkeybrain20122 on 2014-02-20
OpenGL 1.4 is rather low so not surprising it is not working. You probably need at least 2.1. That card uses driver i915 from 
[http://askubuntu.com/questions/200995/is-it-possible-to-update-my-graphic-card-drivers](http://askubuntu.com/questions/200995/is-it-possible-to-update-my-graphic-card-drivers) You can confirm it by posting the outputs of 
```
lshw -C display

```
I know that if you upgrade mesa to version 10 i915 would support opengl 2.1 (the answer in link above is outdated) 

There is this ppa for bleeding edge open source drivers so back up your system, install ppa-purge and use at your own risk. If works then should disable the ppa right the way.

[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/) but it only supports Ubuntu 13.10 and 14.04

For 12.04 use [https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers)

12.04 is kind of tricky because of all the point releases and lts graphic stack updates. I am not sure if you have to revert the graphic stack to 12.04.0's state first in order to apply this ppa (say you have installed 12.04.3) or it will break your display (e.g xorg-edgers would if you have the newer 12.04 point releases)  Better clarify with the ppa maintainer first.

If mesa 9.2 works then you can go a safer route [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
But you should ask someone who uses Ubuntu 13.10 and i915 what his/her opengl version is.

---


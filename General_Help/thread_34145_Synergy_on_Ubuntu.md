---
title: "Synergy on Ubuntu?"
date: 2005-05-13
forum: General Help
---

### Post by rotten on 2005-05-13
I'm a big fan these days of the keyboard/mouse sharing utility "synergy" - [http://sourceforge.net/projects/synergy2](http://sourceforge.net/projects/synergy2) 

(Even with its relatively minor quirks.)

So naturally the first thing I go to do when I built my first Ubuntu machine today was to install it.

For some reason, however, it can't find the X libraries when I run configure.
I've tried pointing to them with the relevant configure options (--x-libraries), and I've tried setting LD_LIBRARY_PATH.

I'm open to suggestions as to why this software might be having so much trouble getting configured, and any possible work around.

---

### Post by dschep on 2005-06-29
To get synergy working on my ubuntu (hoary) install I temporarily added the breezy repositories to my sources.list and installed. THis is because the hoary repository only had an old version for which there is no compatiple binary on the mac. Of course when done comment out the breezy sources and update again.

---

### Post by aaarg on 2005-07-05
did it work? synergy looks great and i am considering using synergy myself.....

---

### Post by OuchIAteMyself on 2005-07-11
[QUOTE=dschep]To get synergy working on my ubuntu (hoary) install I temporarily added the breezy repositories to my sources.list and installed. THis is because the hoary repository only had an old version for which there is no compatiple binary on the mac. Of course when done comment out the breezy sources and update again.[/QUOTE]


I tried adding the breezy repositories to my list and noticed that 460 updates were available, so I went ahead and installed. The alien install works as usual, but I'm getting the same error still.

Any speculations as-to what I did wrong?

Thank you so much for your help.

---

### Post by kleeman on 2005-07-11
I compiled and installed it from source fine from hoary. Going to breezy would seem a pretty radical (and possibly unwise) step to me. The key package I had to install in order to get it to compile was libxtst-dev which I found using synaptic.

---

### Post by OuchIAteMyself on 2005-07-11
[QUOTE=kleeman]I compiled and installed it from source fine from hoary. Going to breezy would seem a pretty radical (and possibly unwise) step to me. The key package I had to install in order to get it to compile was libxtst-dev which I found using synaptic.[/QUOTE]


When I try to build from source, it says it can't find the compiler.

When I use alien to install the RPM it installs fine, but I get this:

synergyc: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

 :-|

This is frustrating me to no end b/c it installed on Fedora w/o a hitch... *sigh*

---

### Post by kleeman on 2005-07-11
See the Unofficial Starter Guide for installing compilers:

[http://ubuntuguide.org/#build-essential](http://ubuntuguide.org/#build-essential)

---

### Post by OuchIAteMyself on 2005-07-11
[QUOTE=kleeman]See the Unofficial Starter Guide for installing compilers:

[http://ubuntuguide.org/#build-essential](http://ubuntuguide.org/#build-essential)[/QUOTE]
  #-o  thank you.......

---


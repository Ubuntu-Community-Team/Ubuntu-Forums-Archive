---
title: "beagle error"
date: 2005-06-08
forum: General Help
---

### Post by brickbat on 2005-06-08
Hi, When I installed beagle from the repo I got this error;

** (/usr/lib/beagle/Best.exe:6531): WARNING **: The following assembly reference d from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/beagle).


** (/usr/lib/beagle/Best.exe:6531): WARNING **: The class Gecko.WebControl could  not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be re ached
aborting...
Aborted


Would appreciate some help pls.

ciao
bb

---

### Post by kori.mendocino on 2005-06-08
hmm, are you sure that you have installed all the packages that beagle requires in order to compile and run ok? check [this](http://beaglewiki.org/Ubuntu_Installation) out, under 'hoary instructions'. it *should* help you out

---


---
title: "Mono App Issues in Edgy"
date: 2006-12-27
forum: General Help
---

### Post by j o e l on 2006-12-27
Hello.  I began using Edgy a few weeks ago and have had a difficult time trying to get a couple Mono apps working.  Both Banshee and F-spot crash during startup and seem to give to indicate there are missing libraries, despite the fact I've tried to build-dep both and manually install each library that I am aware of.  Basically, both seem to indicate gnome-sharp can't be found...
**_F-Spot_**
> joel@baseCamp2go:~$ f-spot

** (/usr/lib/f-spot/f-spot.exe:8023): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=9)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:8023): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.



Is there some way to list what packages/libraries you have to double-check?  I'm still fairly new to Linux, so I'm not always sure what to do in troubleshooting these kinds of things.

Thanks for any assistance you might be able to give...

---


---
title: "Missing libraries: libOpenImageIO"
date: 2014-04-06
forum: General Help
---

### Post by javierdl on 2014-04-06
Hi all,

I got this error while trying to run a program I had just expanded: 
Terminal feedback:
./blender: error while loading shared libraries: libOpenImageIO.so.1.4: cannot open shared object file: No such file or directory

Unfortunately both Software Center & Synoptic seem outdated as they only offer version 1.3. I went to [PKGS.org]("http://pkgs.org/search/?query=libOpenImageIO&type=smart"), but they also only have up to 1.3. 
Should I infer that 1.4 is only available for Ubuntu 14?

Thanks guys,

JDL

---

### Post by Spirou4D on 2014-05-28
Hi friend,

I have the same problem with my blender GSOC 2013 by Antony Riakiotakis and I sended him several questions about this compilation.
It's weird!

Wait and see...

I take you in wave...
Bye
Spirou4D

PS: I have ubuntu 14.04 in linux Mint Qiana 17 on AMD64 and the same problem!

---

### Post by mc4man on 2014-05-28
1.3 is the latest in Ubuntu thru current 14.10 dev. So it you got blender from a ppa then it should provide the proper openimageio version packages. 
If gotten elsewhere then look into providing your own openimageio build or try below - 

As far as packaged versions of 1.4 this ppa does have - 
[https://launchpad.net/~irie/+archive/blender](https://launchpad.net/~irie/+archive/blender)

---


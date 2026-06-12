---
title: "Jurassic Park-style 3D FS navigation (&quot;This is Unix! I know this!&quot;)"
date: 2006-12-09
forum: General Help
---

### Post by escape on 2006-12-09
I believe [this]("http://www.sgi.com/fun/freeware/3d_navigator.html") is what is used in Jurassic Park as the desktop manager (is it even that?) for the 3D filesystem display. You'll note that was designed for IRIX, which as far as I know means !Linux which means !Ubuntu. Does anyone know of a port of FSN ("File System Navigator") for Linux/Ubuntu? There's [this thing]("http://fsv.sourceforge.net/") but it doesn't look exactly the same, although I guess it's the official port. I've checked out [this site]("http://nooface.net/3dui.shtml") already as well, but still, not really what I'm looking for. Is there anything like this in the repositories? I've seen fsviewer but as far as I can tell it's not in 3D. I know this isn't really practical, but it would be kind of cool to have...


Update: I think I'm just going to use fsv

---

### Post by cookfromfrozen on 2006-12-09
Damn that would be so cool.  For the effect I'd imagine there are a bunch of veliciraptors trying to break down my door while I'm browsing through my directory hierarchy.

The IRIX visualiser is definitely what they used in Jurassic Park though since they used mostly SGI systems both in the film and to produce it.  AFAIK there's nothing like this in the repos.

IRIX is not Linux but as far as I know IRIX uses the X Window System so in theory it should work, but fsv should work a little better.  I think I'd try fsv.

"Reboot the door locks!"

---

### Post by cookfromfrozen on 2006-12-09
Here's a deb (attached) I built with checkinstall from the fsv source code if you need it.  It seems to work pretty well although you might need some openGL libraries, I'm not sure.

The IRIX fsn is a precompiled binary but for some reason I can't get it to work.  I'll keep trying though.

---

### Post by escape on 2006-12-15
Thanks for the deb. Even thoug I have the libgtkgl* libraries installed, I got compile time errors with the source for those "missing" dependencies, and get the same problem when running the deb.  This time it can't find libgtkgl.so.5; I'm not gonna worry much about it tho. Thanks again.

---

### Post by nelefa on 2008-02-02
> **escape said:**
> I believe [this]("http://www.sgi.com/fun/freeware/3d_navigator.html") is what is used in Jurassic Park as the desktop manager (is it even that?) for the 3D filesystem display. You'll note that was designed for IRIX, which as far as I know means !Linux which means !Ubuntu. Does anyone know of a port of FSN ("File System Navigator") for Linux/Ubuntu? There's [this thing]("http://fsv.sourceforge.net/") but it doesn't look exactly the same, although I guess it's the official port. I've checked out [this site]("http://nooface.net/3dui.shtml") already as well, but still, not really what I'm looking for. Is there anything like this in the repositories? I've seen fsviewer but as far as I can tell it's not in 3D. I know this isn't really practical, but it would be kind of cool to have...


Update: I think I'm just going to use fsv

I used this file manager (as a novelty) on an IRIX6.2 box back in the day and it was completely unusable. Even on a fairly perky SGI O2, is took a ridiculous time to do the equivalent of cd /usr/local/bin :)

Choobs

---

### Post by divideoverflow on 2008-05-09
I figured I'd chime in as my first post. I also wanted to try FSV after remembering seeing FSN back in Jurassic Park. The deb attached works fine, it's just missing one dependency, gtkglarea5, which includes the shared object libgtkgl.so.5 required by FSV. After installing this from the Universe repos on Hardy, it works fine. My mismatched dual monitors kinda throws off the app, but it's better than nothing.

---

### Post by angry_johnnie on 2008-05-10
I have an aliened package of the aforementioned libgtkglarea5 (couldn't find it in the repos).

---


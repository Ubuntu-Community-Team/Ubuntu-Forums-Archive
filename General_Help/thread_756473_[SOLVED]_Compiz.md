---
title: "[SOLVED] Compiz"
date: 2008-04-15
forum: General Help
---

### Post by Gripp on 2008-04-15
i tried getting Compiz running.  first, i tried the "supported application" versions installed from the add/remove applications menu. 

it seems to have done nothing.  i went to /usr/bin/compiz and ran it thru the terminal, it complains that it doesn't have XGL playning with it, and then does nothing else.  

so i tried the unsupported configuration tool, with the previous tool.
that gave me the config GUI, but didn't do anythin, then i tried without the "supported" tool still nothing
if anything, if i actually have it switch from meta-whatever to compiz it hoses my desktop til i switch back

point being, i cant get it to work at all - not one feature.  
is this because i'm working from Wubi?  or maybe that my video drivers are based on windows drivers (nVidia 880GTX) or that i'm a complete noob in linux? :P

---

### Post by ago on 2008-04-16
No wubi has nothing to do with Compiz. More likely you do not have the appropriate video driver and/or video configuration. I would suggest to follow this up in the general Ubuntu forum, Wubi work is done as far as I can tell :)

---

### Post by chewearn on 2008-04-16
> **Gripp said:**
> ... it complains that it doesn't have XGL playning with it, and then does nothing else.  

This, in fact, means you don't have the nvidia restricted driver installed (i.e. 3D support not enabled).

> is this because i'm working from Wubi?  or maybe that my video drivers are based on windows drivers (nVidia 880GTX) ...That is a misunderstanding.  With wubi, it only means you are using Windows to bootstrap the ubuntu boot.  After ubuntu is started, everything from there is fully linux.  That means the Windows nvidia driver is not used (this not possible anyway).

What you need to do is enabled the nvidia restricted driver in the Restricted Driver Manager (Hardware Drivers icon in Hardy).

---

### Post by Gripp on 2008-04-16
yeah, i just installed the openGL drivers and everything works great.

compiz is soo great.  hours of entertainment :D

---


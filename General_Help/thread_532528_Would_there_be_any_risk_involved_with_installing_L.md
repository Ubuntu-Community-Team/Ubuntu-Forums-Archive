---
title: "Would there be any risk involved with installing Lubi in Wubi?"
date: 2007-08-22
forum: General Help
---

### Post by Romanus81 on 2007-08-22
Is it possible to install Lubi in Wubi? I want to create a completely seperate Ubuntu install so that, if I need to do a lot of tinkering to get something to work, I can at least try it out to see if I can get it working before I try it on my normal Ubuntu install? 
I tried doing what the wiki said, and renaming system.virtual.disk, and going through the wubi installer, but ended up clearing my /home directory. Is there a different way?

---

### Post by tuxcantfly on 2007-08-22
> Would there be any risk involved with installing Lubi in Wubi?

Simply wouldn't work; grub wouldn't be able to boot the double-loopmounted install. What I'd do is first shrink your existing partitions and create new ones, upgrade to a real install with LVPM, then use Lubi to make a tinker-install. Details at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---


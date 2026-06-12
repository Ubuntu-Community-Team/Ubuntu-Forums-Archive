---
title: "Beryl Freezing GNOME"
date: 2006-11-26
forum: General Help
---

### Post by BarfBag on 2006-11-26
[I installed Beryl by following the instructions in this guide.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29")

When I type beryl-manager to start it up, the window borders for every window I have open disappear and the entire desktop freezes up.  I see the little red gem icon pop up next to the clock before this happens.  How do I fix this?

I have a brand new nVidia video card with the driver installed.

---

### Post by junglepeanut on 2006-11-26
Have you checked if the driver is bieng used? I dont know the command for nvidia, so please check i.e. ati=fglrxinfo

Also check if you have direct rendering 
glxinfo 
should say yes for direct rendering at the top.

---

### Post by PrinceArithon on 2006-11-26
I had this same problem and found the solution here in the forums somewhere.  The best I can tell you is go to the search bar and type in the word beryl.

That's all I did and after a few searches I found the answer.  It's a real simple fix.

---


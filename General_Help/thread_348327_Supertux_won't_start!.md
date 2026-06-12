---
title: "Supertux won't start!"
date: 2007-01-28
forum: General Help
---

### Post by daz4126 on 2007-01-28
Hi,

When I try to run supertux from the terminal, I get the following error message:

```
Invalid button '0' in buttonmap
Invalid button '1' in buttonmap
Fatal: Unexpected exception: Couldn't set video mode (800x600-0bpp): Couldn't find matching GLX visual
```

Anybody know a) what this means and b) how to fix it??

thanks,

DAZ

---

### Post by taurus on 2007-01-28
Looks like supertux wants to run it in a lower resolution than you are currently using.  Maybe change the "DefaultDepth    24" in /etc/X11/xorg.conf to "DefaultDepth    16"!

---

### Post by daz4126 on 2007-03-02
Hi,
Thanks for the reply. I fixed this by editing the config file so that the game starts up in a window rather than full screen. Thanks again.

DAZ

---

### Post by lmpmbernardo on 2008-02-02
how do you do that? supertux -w -g 800x600?

[lmpmbernardo@antonio ~]$ supertux -w -g 800x600
[/home/lmpmbernardo/.supertux2] is in the search path
[/usr/share/supertux] is in the search path
Invalid button '0' in buttonmap
Invalid button '1' in buttonmap
Fatal: Unexpected exception: Couldn't set video mode (800x600-0bpp): Couldn't find matching GLX visual
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  79 (X_FreeColormap)
  Resource id in failed request:  0x4400001
  Serial number of failed request:  86
  Current serial number in output stream:  87
*** glibc detected *** supertux: double free or corruption (out): 0x08e598b0 ***
...................................

---

### Post by daz4126 on 2008-02-03
I found the config file in my home directory (it is hidden and called something like supertux2). You can then set fullscreen to false.

Hope that helps,

DAZ

---

### Post by lmpmbernardo on 2008-02-04
Thanks. I figured out I had a problem bigger than Supertux. Other applications that use 3D were not starting either. The problem was due to the nvidia card I had just gotten the the nvidia proprietary drivers that I initially installed. Removing them and replacing them by the drivers provided by the distro fixed the problem. The proprietary drivers had overwritten some OpenGL files that stuff like Supertux and Celestia need. I still have problems with constant freeze ups of the machine though...

---

### Post by anway on 2008-04-17
I encount the same problem.

I have change the config file.but the problem have not resolve.

maybe this is caused by TNT drivers.

---


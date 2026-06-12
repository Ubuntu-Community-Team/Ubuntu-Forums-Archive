---
title: "Problems with openGL"
date: 2007-02-08
forum: General Help
---

### Post by IronArjen on 2007-02-08
I have two problems that I believe to be caused by the same: something is wrong with my openGL. 1 I cannot run a certain software that is basically a GUI on top of a functioning software. 2 I cannot run wine.

Code 1

arjen@beavis:/media/win$ clustalx
Couldn't find X visual appropriate for OpenGL!

Code 2

arjen@beavis:/media/win$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

Then a check, Code:

arjen@beavis:/media/win$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None

Other check that I ran into in a page describing Wine for 64AMD (my case)

arjen@beavis:/media/win$ glxgears
Error: couldn't get an RGB, Double-buffered visual

I tried to find information about this GLXgears but only find it in threads where they apparently understand what they are doing (I don't!)

Thanks

---

### Post by MoLE on 2007-02-16
Ok, you need to let us know what sort of video hardware you are using.  Quickest way to do this is open the terminal and give us the output of:
```
lspci | grep VGA
```

The we can point you in the right direction to get 3d-acceleration (GLX support) going on your system.

---

### Post by IronArjen on 2007-02-20
I get no output!

arjen@beavis:~$ lspci | grep VGP
arjen@beavis:~$


With video hardware you refer to video card? I have an onboard video carc since I use only  simple graphical stuff, no games etc.

---

### Post by Maestro23 on 2007-02-20
> **IronArjen said:**
> I get no output!

arjen@beavis:~$ lspci | grep VGP
arjen@beavis:~$


With video hardware you refer to video card? I have an onboard video carc since I use only  simple graphical stuff, no games etc.

lspci | grep VGA

---

### Post by IronArjen on 2007-02-20
OK!

arjen@beavis:~$ lspci | grep VGA
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
arjen@beavis:~$

---

### Post by MoLE on 2007-02-21
Sorry, my typo originally.

Looks like your chipset is supported by the latest nvidia drivers.  You can install the version in the ubuntu repositories (which should be fine for day-to-day stuff), by executing the following:
```
$ sudo aptitude install nvidia-glx
```
then once installed, execute the following:
```
$ sudo nvidia-glx-config enable
```

You must have the restricted, universe and multiverse repositories enabled and refreshed before you do this.  You can check this has been done through System --> Administration --> Software Sources.

---

### Post by IronArjen on 2007-02-21
YES! Both wine and clustalX work, really great. This forum is great! Thanks a bunch.

I guess what I did was reconfigure my X better towards my video? (Like to know what I am doing so next time I might figure it out myself!)

---


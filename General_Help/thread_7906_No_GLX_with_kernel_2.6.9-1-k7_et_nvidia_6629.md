---
title: "No GLX with kernel 2.6.9-1-k7 et nvidia 6629"
date: 2004-12-12
forum: General Help
---

### Post by ploum on 2004-12-12
Hello,

I just upgraded my kernel today to 2.6.9-1-k7 and the nvidia driver to 1.6629, using synaptic (I'm in Hoary).

I've also upgraded restricted-components

```
apt-cache policy linux-restricted-modules-2.6.9-1-k7
linux-restricted-modules-2.6.9-1-k7:
  Installés : 2.6.9-6
  Candidat : 2.6.9-6

```

After a reboot under the new kernel, GLX is not working anymore !  After some googling, I've added the following line :

```
Option          "AllowGLXWithComposite" "true"
``` 

But nothing has changed :-(  I've also fully commented out the lines about CompositeManager to disable it, no more succes.

I've no more GLX.

```

$xdpyinfo|grep GLX                                   
    NV-GLX

```

from Xorg.log :
```

(II) Loading extension NV-CONTROL
(EE) NVIDIA(0): Failed to load GLX
(WW) NVIDIA(0): Option "AGPFastWrite" is not used
(==) RandR enabled

```


Any idea ?  I suppose this is a very dumb thing...  I just want to play gl-117 ;-)

---

### Post by SepheeBear on 2004-12-13
Yeah I've run into the same issue with the latest nvidia binaries. It seems the culprit is a broken link belonging to the "nvidia-glx" package. 

[SIZE=2]ls -l /usr/X11R6/lib/modules/extensions/libglx*

lrwxrwxrwx  1 root root     10 2004-12-13 01:01 [COLOR=Red]/usr/X11R6/lib/modules/extensions/libglx.so[/COLOR] -> libglx.so.
-rw-r--r--  1 root root 573988 2004-12-11 08:10 /usr/X11R6/lib/modules/extensions/libglx.so.1.0.6629[/SIZE]

Problem is when I tried redoing the link to point to "./libglx.so.1.0.6629" I still could not start X. Even after deleting this altogether X still wouldnt start. Putting everything back with the link still broken was the only way I could get X to start successfully. So for the time being I'm leaving it broken (no Flipscreen3d screensaver for me tonight  :sad: )

Maybe later I'll try building glx from "nvidia-kernel-source" but Im no gamer so it's no priority. It'll likely be fixed soon before I get to it anyway. The Ubuntu Devels rock!

As a sidenote mplayer stopped functioning after this update as well. Just gives error "Segmentation fault". Could be a coincidence.

---

### Post by ploum on 2004-12-13
indeed. I've tried without success.

It's strange because the X server crashes without any (EE) when "Initializing GLX"

I will wait :-)

---

### Post by daniels on 2004-12-13
Oops.  Good catch, thanks.

---

### Post by subjectdenied on 2004-12-13
[QUOTE=daniels]Oops.  Good catch, thanks.[/QUOTE]
 i had the some problems, and got it working again by removing the ubuntu nvidia-kernel-module and the glx-driver completely

after that i installed the nvidia-drivers from the nvidia-website, and everything's working again

---

### Post by daniels on 2004-12-13
I'm working on a new version now; I think I've got it, just need to run some more tests thorugh it.

Maintaining l-r-m (and thus nvidia-glx) when you don't own any nVidia hardware is kinda difficult. ;)

---

### Post by ploum on 2004-12-13
[QUOTE=daniels]I'm working on a new version now; I think I've got it, just need to run some more tests thorugh it.

Maintaining l-r-m (and thus nvidia-glx) when you don't own any nVidia hardware is kinda difficult. ;)[/QUOTE]
 I understand that it's quite difficult ;-)

If it can help you, I can use [http://people.ubuntu.com/~daniels/l-r-m/i386/](http://people.ubuntu.com/~daniels/l-r-m/i386/) and upgrade often, so you can have bug reports before it enters to Hoary.

---

### Post by ploum on 2004-12-13
I've tried the latest deb package available at  [http://people.ubuntu.com/~daniels/l-r-m/i386/](http://people.ubuntu.com/~daniels/l-r-m/i386/) but it doesn't work ...

lrwxrwxrwx  1 root root   18 2004-12-13 14:42 libglx.so -> libglx.so.1.0-6629
-rw-r--r--  1 root root 561K 2004-11-25 19:58 libglx.so.1.0.6629

This time, the error is a "-" instead of a "."

Changing manually the link crash the server, as seen before.

---

### Post by daniels on 2004-12-13
The stuff on p.u.c is outdated; I have a version here that hopefully fixes that.

---

### Post by ploum on 2004-12-27
Is there any trick to solve temporary this problem ? Anyone ? (Or does it must be corrected and I did something wrong?)

---

### Post by jbh on 2005-01-01
I upgraded my warty amd64 kernel and my nvidia drivers stopped working mysteriously too.. so all I did was d/l drivers from [www.nvidia.com](www.nvidia.com) and run the install program again. bizzang worked.

---

### Post by jbh on 2005-01-02
when i tried installing the nvidia drivers into a 32bit chroot I made I got the same problem with the k7 kernel :(

---

### Post by kokos4151 on 2007-05-15
> **ploum said:**
> Hello,

I just upgraded my kernel today to 2.6.9-1-k7 and the nvidia driver to 1.6629, using synaptic (I'm in Hoary).

I've also upgraded restricted-components

```
apt-cache policy linux-restricted-modules-2.6.9-1-k7
linux-restricted-modules-2.6.9-1-k7:
  Installés : 2.6.9-6
  Candidat : 2.6.9-6

```

After a reboot under the new kernel, GLX is not working anymore !  After some googling, I've added the following line :

```
Option          &quot;AllowGLXWithComposite&quot; &quot;true&quot;
``` 

But nothing has changed :-(  I've also fully commented out the lines about CompositeManager to disable it, no more succes.

I've no more GLX.

```

$xdpyinfo|grep GLX                                   
    NV-GLX

```

from Xorg.log :
```

(II) Loading extension NV-CONTROL
(EE) NVIDIA(0): Failed to load GLX
(WW) NVIDIA(0): Option &quot;AGPFastWrite&quot; is not used
(==) RandR enabled

```


Any idea ?  I suppose this is a very dumb thing...  I just want to play gl-117 ;-)


[Loans bread pollution solar skin treatment](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---


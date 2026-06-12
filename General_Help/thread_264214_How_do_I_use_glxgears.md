---
title: "How do I use glxgears?"
date: 2006-09-24
forum: General Help
---

### Post by UltraSonicSite on 2006-09-24
When I type it in the console some gears pop out, but no framerate is shown.

---

### Post by TigerCR1200 on 2006-09-24
Type glxgears -printfps that should get you the results you are looking for.

---

### Post by UltraSonicSite on 2006-09-24
nothing's displayed. Just normal gears.

---

### Post by ~LoKe on 2006-09-24
Have you tried waiting a few seconds?

---

### Post by mac57 on 2006-09-24
Folks, it may or may not be relevant, but I had the same experience. I used easyubuntu to upgrade to the latest nvidia driver. I quickly discovered that easyubuntu had NOT updated my xorg.conf file. In particular, it had not changed "nv" to "nvidia" and had not deleted the Modules entry 

Load "dri"

So, glxgears, while it would run, would just report errors.  I fixed the above, and tried again. This time, per the original poster here, no results. I got the glxgears display, but no print out. glxgears does not conform to Linux norms. None of:

man glxgears
glxgears -h
glxgears --help

produced any help on available options. However, per another of the above posts, when I added the "-printfps" option, it started to work as it does in other Linux releases (who must have set up an alias I am guessing). 

I go through this whole tale of woe just in case the original poster has a combination of these things going on.

By the way, on my 3.0 GHz Pentium IV HT, using a GeForce 4 TI 4200, I am getting an average glxgears score of 3670.

Hope this helps!

---

### Post by Rui Pais on 2006-09-24
> **UltraSonicSite said:**
> nothing's displayed. Just normal gears.

try
```
 glxgears -info
```

---

### Post by dcstar on 2006-09-24
"strings /usr/bin/glxgears" provides the following (mixed in with the rest):

@-display
-info
-stereo
-fullscreen
-iacknowledgethatthistoolisnotabenchmark
-printfps

---


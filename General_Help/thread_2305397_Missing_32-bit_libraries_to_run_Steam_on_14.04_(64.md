---
title: "Missing 32-bit libraries to run Steam on 14.04 (64-bit)"
date: 2015-12-05
forum: General Help
---

### Post by Hugo_Vaillancourt on 2015-12-05
I've been using 14.04 (64-bit) on my Lenovo Thinkpad T420 for about a year, and I never had any issues running Steam. Recently, I had to reinstall Ubuntu, and after I reinstalled Steam (from their website package) and tried running it, I got the following message:

Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386

It then tries to install them, but fails. I get a message that some packages are missing dependencies (I run Ubuntu in French, but I'm including this so people can see the package names):

Les paquets suivants contiennent des dépendances non satisfaites :
 libgl1-mesa-glx:i386 : Dépend: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
 unity-control-center : Dépend: libcheese-gtk23 (>= 3.4.0) mais ne sera pas installé
                        Dépend: libcheese7 (>= 3.0.1) mais ne sera pas installé
E: Erreur, pkgProblem::Resolve a généré des ruptures, ce qui a pu être causé par les paquets devant être gardés en l'état.

The thing is, when I try to install libglapi-mesa, libcheese-gtk23, and libcheese7, APT tells me they're already there. I've tried a number of older fixes (dating back to last spring) for similar issues with Steam, but nothing worked. I've submitted a ticket to Steam support a few days back, but they have yet to reply to it. Are these libraries unavailable now? Am I missing repositories? Or is this something else altogether?

Thanks!

---

### Post by Ricardo_Velasco on 2015-12-05
Greeting:

Here is an issue solved as Steam operating systems installed on 64-bit Ubuntu .

Read it and tell me if it works :


[http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)

---


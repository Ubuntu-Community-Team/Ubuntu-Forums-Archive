---
title: "Old WIne"
date: 2006-07-16
forum: General Help
---

### Post by thunderduck3141 on 2006-07-16
i need to get wine version 0.9.13 on my system, i currently have 0.9.17
is there anyway i cann have both exist one system?
and where would i get the older version?
thanks in advance

---

### Post by YokoZar on 2006-07-18
You can now easily get old Wine packages by downloading them from the [WineHQ packages archive](http://wine.budgetdedicated.com/archive/index.html).  Just download the version you're looking for.

Now, if it truly is the case that your program works in an old version of Wine but not in the current version, then you have discovered what we call a *regression*.  Regressions are quite serious bugs, as if they go unreported apps can sometimes remain broken for *very* long amounts of time - Fallout 2, for instance, worked fine in 2002 and then became broken for over a year due to an unreported regression in Wine's Direct Input handling.

So, please, do us all a favor and [file a bug](http://bugs.winehq.org/) or send an email to the [wine-devel mailing list](http://winehq.org/site/forums) noting that you have found a "regression".

Anyway, I hope you can get it working again, and if you need help installing the old packages, just ask here.

---

### Post by thunderduck3141 on 2006-07-18
what i mean to say is is it possible for me to have both wine 0.9.13 and 0.9.17 on the same system, and lets say name one of them wine2 so i could go like this

wine aom.exe

or

wine2 aom.exe

and each have its own .wine directory
and the regression has been reported

---

### Post by YokoZar on 2006-07-18
> **thunderduck3141 said:**
> what i mean to say is is it possible for me to have both wine 0.9.13 and 0.9.17 on the same system, and lets say name one of them wine2 so i could go like this

wine aom.exe

or

wine2 aom.exe

and each have its own .wine directory
and the regression has been reported
While this is possible, it is by far a lot less work to simply keep both versions of the package around and just install the old one when you need it.

---

### Post by thunderduck3141 on 2006-07-18
if it is possible how is it done

---

### Post by RAOF on 2006-07-19
> **thunderduck3141 said:**
> if it is possible how is it done

By "While this is possible, it is by far a lot less work to simply keep both versions of the package around and just install the old one when you need it.", I believe he meant: If you need to ask, you don't want to do it :)

One way you could do it would be to install one version of wine, move all the installed files (including .wine directory) somewhere else, then install the second version of wine and do the same thing.  Then write a couple of scripts, wine1 & wine2 which symlink the appropriate wine files, then call wine.  This would probably require root privilages where appropriate, and generally be much more difficult than just installing the appropriate version before running your program!

---

### Post by thunderduck3141 on 2006-07-19
eh, it will give me something to do
thanks a bunch 
...
2000 post, Jesus

---

### Post by socratesgdl on 2008-04-03
I was using wine 9.48 WITHOUT troubles in TERATERM PRO ver. 2.3,,,but NOW with WINE 9.58.....teraterm DOESNT WORK!!

WHY????

---

### Post by socratesgdl on 2008-04-03
I was using wine 9.48 WITHOUT troubles in TERATERM PRO ver. 2.3,,,but NOW with WINE 9.58.....teraterm DOESNT WORK!!

WHY????

---


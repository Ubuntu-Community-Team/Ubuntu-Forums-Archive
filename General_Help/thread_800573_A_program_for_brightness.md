---
title: "A program for brightness?"
date: 2008-05-20
forum: General Help
---

### Post by AmenX on 2008-05-20
I was wondering if there was a program out there that I could use to adjust my gamma/brightness/contrast.

I need one that will do all of those.
My monitor is dark, and there isn't relly a way to make it look good without editing that, but I haven't been able to find anything for Ubuntu that will change it.

Someone please help. :(

---

### Post by sdennie on 2008-05-20
I believe that is graphics card specific.  If you are using an nvidia card and have the restricted drivers installed, you can go to a terminal and type:

```

nvidia-settings

```

The settings you are looking for will be under the color corrections section.

---

### Post by AmenX on 2008-05-20
I have an ATI card.
But, for some reason the drivers won't install. :(

---

### Post by knutschr on 2008-05-20
> **AmenX said:**
> I have an ATI card.
But, for some reason the drivers won't install. :(

Read this:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by mc4man on 2008-05-21
While searching the filesystem for files related to DDC I noticed an app mentioned in app-install - gddccontrol. (not installed ) It allows you to do most monitor adjustments thru a gui. If it doesn't find your monitor in the database I'd limit using it to the basic adjustments. (opens with gksu gddccontrol ) maybe there's a more recent similar app?
Gamma can be adjusted by running in terminal xgamma -gamma x.xxx the default for x.xxx is 1.000  You can go higher or lower or adjust red, green, blue individually. See xgamma --help .The gamma setting only last till you reboot. 
Technically you should be able to make gamma changes permanent in xorg.conf, though i don't think it jives to well with the current xorg-7.3 and auto detection.?

---


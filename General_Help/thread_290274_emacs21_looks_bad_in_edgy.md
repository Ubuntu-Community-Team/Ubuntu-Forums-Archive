---
title: "emacs21 looks bad in edgy"
date: 2006-11-01
forum: General Help
---

### Post by rpk180 on 2006-11-01
I upgraded to edgy a few days ago.  Everything went smoothly.  However, emacs21 now looks really bad.  The font is small and very hard to read (see attached screenshot).

I've tried some of the hints in this thread (with no luck): [http://www.ubuntuforums.org/showthread.php?t=77591&highlight=emacs21](http://www.ubuntuforums.org/showthread.php?t=77591&highlight=emacs21)

Any ideas on how to make it look good again?

---

### Post by Rui Pais on 2006-11-01
you probably have the common font problem in edgy

try the suggestions [here]("http://ubuntuforums.org/showthread.php?p=1673121#post1673121").

---

### Post by rpk180 on 2006-11-03
Thank you for the suggestion, but none of the hints in that thread helped me.  I tried the following:

 - dpkg-reconfigure xserver-xorg (and use the VESA driver)
 - Enabling subpixel smoothing and subpixel Hinting
 - Adding a fonts.conf file to my home directory (as outlined in this thread: [http://www.ubuntuforums.org/showthread.php?t=272470&page=6](http://www.ubuntuforums.org/showthread.php?t=272470&page=6))

I ended up installing xemacs and it looks pretty good.  For now, that will  have to be my workaround.  However, I would prefer to use emacs because that is what I'm used to.

---

### Post by Rui Pais on 2006-11-14
Hi, 
did you solve it the issue by now?

Check if [this thread]("http://www.ubuntuforums.org/showthread.php?t=285304") helps.

---

### Post by rpk180 on 2006-11-16
That [thread]("http://www.ubuntuforums.org/showthread.php?t=285304") had the answer.  Changing the font paths in xorg.conf from "/usr/share/X11/fonts/..." to "/usr/share/fonts/X11/..." and restarting did the trick!!!

Thank you Rui Pais!

---

### Post by Rui Pais on 2006-11-16
> **rpk180 said:**
> That [thread]("http://www.ubuntuforums.org/showthread.php?t=285304") had the answer.  Changing the font paths in xorg.conf from "/usr/share/X11/fonts/..." to "/usr/share/fonts/X11/..." and restarting did the trick!!!

Thank you Rui Pais!
Glad it helped :)

(it was something so simple and i fail to see it for so long... ](*,) )

---


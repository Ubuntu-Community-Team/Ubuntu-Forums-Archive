---
title: "I've really done it now... xorg.conf death"
date: 2008-06-20
forum: General Help
---

### Post by amishphysicist on 2008-06-20
Hey All,

Let's get this out of the way first, I know I blew it by not backing up my xorg.conf file before trying something out, so I'm very sorry.

Here's the output from the compiz checker
```
 
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
 Driver in use:         vesa
 Rendering method:      AIGLX

```

A little background and my issue:

I was fiddling with firefox and it kept crashing (and staying crashed until a full restart) with google reader and flash.  I found a bunch of threads telling me that all I had to do was edit xorg.conf and change my DefaultDepth to 24, and it would magically fix all my crash bugs.

Upon restart, Ubuntu came up in this very sad little graphics mode and told me to try to re-pick my monitor, etc.

I've since restored back to the failsafe xorg.conf and managed to get my monitor up to 1280/1024, but I've lost the following:

1) Mousewheel over the desktop to switch desktops 
     (mousewheel still works to scroll)
2) The ability to enable anything besides the basic graphics modes.
3) The ability to select any drivers for my video card.
4) lord knows what else...

Long story short, I tried fixing Firefox and now my Ubuntu is in ugly land, and I'm a bad person for not backing things up.

Thanks,

-nate

---

### Post by MichaelSwengel on 2008-06-20
Oooh...I've been there. Sorry to hear you're having trouble.

Have you tried running the Recovery Mode? (I don't remember the exact name of it.) That should be available from the GRUB menu.

From there, you should (*should*) be able to have some measure of success in fixing issues.

Let us know what happens.

Regards,
MS

P.S. I like your name :D

---

### Post by bubba_169 on 2008-06-20
Was the xorg.conf working perfectly from when you first installed?

If so one possibility could be to (making sure you back up your current xorg.conf in case anything worse happens) run the live cd, then copy the xorg.conf that it generates from the livecd filesystem to your current system?

---

### Post by Pjotr123 on 2008-06-20
This is how you do it:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

---

### Post by amishphysicist on 2008-06-20
**Pjotr123:**
Totally worked.  Fixed everything!  Thanks everyone.

---

### Post by MichaelSwengel on 2008-06-20
We're glad to help, Amishphysicist. That's what Ubuntu is all about. :D 

Cheers,
MS

---

### Post by amishphysicist on 2008-06-20
Hell yeah!  I've had a number of perplexing issues so far and have had nothing but great help.  The community here is 90% of why Ubuntu is so great.

---


---
title: "Just a Question Really........"
date: 2008-07-07
forum: General Help
---

### Post by Kaneda187 on 2008-07-07
I have a problem with my sound, Heres the question....

When im playing music (via amarok) is it normal to have no sound on other apps like flash vids on firefox and no sounds out of aMSN too? can this be fixed?? :confused:

Thanks in advance:)

---

### Post by blackhatbrigade on 2008-07-07
First guess would be to try this:  [http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa)

Try the "Getting more than one application to use the soundcard at the same time" section which is about...  35% down the page.

Hope that works!

---

### Post by mempman on 2008-07-07
> **Kaneda187 said:**
> I have a problem with my sound, Heres the question....

When im playing music (via amarok) is it normal to have no sound on other apps like flash vids on firefox and no sounds out of aMSN too? can this be fixed?? :confused:

Thanks in advance:)

I think the problem that you are having is that your pulseaudio is interfering with flash.  Although there are many ways to solve this problem, I believe the the simplest method is to install  libflashsupport and disallow pulseaudio from being used.

Go to terminal: sudo apt-get install  libflashsupport

and to disallow pulseaudio, do the following:
System->Preferences->Sound
On devices tab, change everything to use "ALSA"
On Sound tab, disable "Enable Software Sound Mixing."

---


---
title: "[SOLVED] GoogleEarth logs out the user"
date: 2007-11-12
forum: General Help
---

### Post by be4truth on 2007-11-12
Hi Everybody,

I have a problem with GoogleEarth on Gutsy 64bit. If I install it via binary or as a deb-installer in both cases when I start it I get logged out. Switching off compiz doesn't make a difference.
Any idea? Or is GoogleEarth only for 32bit?

---

### Post by MichaelSM on 2007-11-30
Hi be4truth.

Same happens with Gutsy 32-bit.

Mike.

---

### Post by oscarsfriend on 2007-11-30
I don't have Gutsy, but this sounds to me like a problem with your X configuration.  I suspect that rather than being logged out, GE is causing the X server to restart (which has the side effect of logging you out).  Try something else with 3D and see what happens.  Try glxgears and glxinfo from a terminal.  And take a look at /var/log/Xorg.0.log.

---

### Post by MichaelSM on 2007-11-30
Thank you oscarsfriend.

I reckon the problem lies in the latest GooglEarth 4,2, even though it's in the repos for Gutsy.

I updated to the latest GE on my Edgy box tonight,,and what used to work doesn't any more....

Rather than Edgy simply refusing to load GE, Gutsy crashes Gnome/X-org as you've read.

There will be something to be fixed soon.

By whom I don't know.

It's probably beyond us basic users at this stage.

Your reply greatly apreciated.

Mike.

---

### Post by be4truth on 2008-01-29
[http://ubuntuforums.org/showthread.php?t=666207]("http://ubuntuforums.org/showthread.php?t=666207")

---


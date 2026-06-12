---
title: "botched libssl0.9.7 install, terminal error messages"
date: 2007-07-17
forum: General Help
---

### Post by sippyCUP on 2007-07-17
I wanted to install linux to use OpenFOAM, so I installed fesity fawn with no problems. I installed OpenFOAM 1.4 per these instructions: [http://ubuntuforums.org/showthread.php?t=156298](http://ubuntuforums.org/showthread.php?t=156298) 

I had a problem running FoamX (the graphical component). It complained that it couldn't find libssl0.9.7, so I went ahead and downloaded all 90 updates that the ubuntu download manager suggested, thinking that libssl might be in there. It wasn't (FoamX returned the same error message), so I went into Synaptic and selected libssl0.9.7. 

After all this, bash wouldn't even recognize the command "FoamX" anymore (:frown:), and on top of that, every time I start the terminal the following 3 error messages appear:

mkdir: cannot create directory `/applications': Permission denied
mkdir: cannot create directory `/applications': Permission denied
mkdir: cannot create directory `/lib//dummy': Permission denied

I don't really know anything about linux but I'm guessing that some installation script is caught in limbo, maybe because my user isn't logged in as su and the appropriate changes can't be initialized. Any ideas?

---

### Post by sippyCUP on 2007-07-17
I created a dummy user account and started the terminal... the error messages do not appear, so it must be a user-specific setting that is causing the problem.  I'm investigating user settings now... any ideas?

---


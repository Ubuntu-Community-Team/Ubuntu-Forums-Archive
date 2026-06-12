---
title: "Help for a relatively uninformed user"
date: 2008-03-21
forum: General Help
---

### Post by esquiador on 2008-03-21
Okay, so let me start this by saying that I'm not the most in-the-know when it comes to command line stuff or how Linux really works. I only started using Ubuntu back in October or so, and it's been great for me so far (except for the minor headache of having a Broadcom wireless card).

But today I decided to install Ubuntu Studio, based on threads recommending it here, overtop of the normal Gutsy installation I already had going on. I did this by going to Synaptic and installing the metapackages ubuntustudio-audio and ubuntustudio-audio-plugins. But they screwed up my computer pretty badly. The graphics seem to be really choppy, especially because it doesn't render webpages nicely when scrolling or loading them. Some icons got screwed up on my panel, and something seems to have overridden my settings in Compiz, because what is going on (window animations, enhanced zoom desktop, etc) doesn't match with the settings.

Also, text sometimes gets turned into nonsense. Like, digital noise looking nonsense, not even just strange letters. In fact it's doing it as I type right now to the words.

Does anybody have any idea what happened, and how to go about fixing it? Short of downloading and burning a CD for a fresh install, I can't think of anything to do.

---

### Post by forrestcupp on 2008-03-21
I'm pretty sure Ubuntu-Studio installs a real time kernel.  If so, try rebooting and choosing to boot to your Generic kernel in the Grub menu.  See if it still happens with the generic kernel.

---

### Post by esquiador on 2008-03-21
Thanks so much. It must have been the real time kernel that was screwing up my settings. Back to the generic kernel for me! That was way simpler to fix than I thought it would be.

---

### Post by forrestcupp on 2008-03-22
It would be nice if you could figure out why.  The real-time kernel is helpful in audio production.  I don't know what to tell you, though.  The only thing that comes to mind is that if you installed your video drivers using Envy, maybe you should use Envy to uninstall them and reinstall them while you're using the real-time kernel to make sure it compiles right.

But you should be ok with the generic kernel, though.  I've done some audio work with Ardour in a generic kernel, and it did ok.

---


---
title: "Enforcing X11 bell volume"
date: 2015-02-07
forum: General Help
---

### Post by jwbrase on 2015-02-07
I have /etc/pulse/default.pa set up so that Pulseaudio intercepts the X11 bell and plays a sound. My problem is that the default bell volume is too low for my liking (set at 50%). The X11 bell volume can be set with "xset b", but the problem is that this does not last for the duration of an X session (otherwise I could set up a script or put xset in .xprofile): it gets set back to the default any time I switch away from tty7. Is there any way of changing the default X11 bell volume so that I don't have to keep manually running xset?

---

### Post by jwbrase on 2015-02-07
On a related note, while I have a bell in terminals running under my X11 session by way of Pulse, I do not have any console bell. I've tried unblacklisting and loading the pcspkr module, to no avail (I'm frankly unsure if my motherboard supports it, given that it's a fairly new board and the PC speaker is a legacy device). Is there any way of getting Pulse to intercept console bell events as it does the X11 bell?

---


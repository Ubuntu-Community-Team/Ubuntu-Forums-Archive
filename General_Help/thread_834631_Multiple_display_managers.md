---
title: "Multiple display managers"
date: 2008-06-19
forum: General Help
---

### Post by InFeh on 2008-06-19
Good day,

I'm wondering if it is at all possible to run both GDM and KDM on one machine simultaneously, hooking both up to its own X server, one on each screen. Is this possible? If so, could I have a neat guide for it?

Humbly awaiting answers,
InFeh.

---

### Post by Sigudian on 2008-06-19
As you sad to me by IM, you have different x-servers allready running on each screen, i think that is an important notice here ;)

---

### Post by InFeh on 2008-06-19
Yes. I've had two X servers tied up to the same display manager for a while. Standard dual-screen set-up. The difference is that I want KDE running on display1 and GNOME running on display0.

---

### Post by lswb on 2008-06-19
Both kdm and gdm can run gnome or kde or other desktops or window managers, you don't need both. If you install both kde and gnome, then you choose which runs from the options menu on the login screen where you enter you user name and password. You will need to be loggied in to 2 sessions for kde and gnome to run simultaneously. I don't have 2 monitors to play with, but I believe you can designate a 2nd monitor to be an Xserver "display" (not sure I'm using the correct terminology) and then it's just a matter of getting gdm or kdm to start X using that display. For that matter, I don't see why you couldn't run, say, kde in a window of a gnome session, or vice-versa, using xephyr or Xnest. Now that's got me thinking...

Good luck!

---

### Post by bodhi.zazen on 2008-06-19
You can do this fairly easily, I do it all the time.

My wife likes KDE / GNOME and I prefer Fluxbox / Openbox ...

So rather then logging off, switching users, just run multiple X sessions.

Now you can only run a single instance of GDM or KDM so to start the other sessions use the command line.

Here is a link you can easily adapt (I hope) :


[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674")

---


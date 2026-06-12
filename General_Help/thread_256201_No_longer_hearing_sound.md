---
title: "No longer hearing sound"
date: 2006-09-12
forum: General Help
---

### Post by stopsatgreen on 2006-09-12
Hi,

I have just installed Democracy Player 0.9, and suddenly most of my programmes have stopped playing sound. VLC, Amarok, etc, don't emit any sound; Rhythmbox does. 

I'm going to take a guess and say that Rhythmbox still plays because it uses Gstreamer and the others don't; but how can I get the rest to play sound?

Should I uninstall Democracy Player and see if that helps? Or do I need to reinstall something else?

---

### Post by stopsatgreen on 2006-09-13
bump

---

### Post by Circus-Killer on 2006-09-13
you can try typing the following in a terminal:
$ killall esd

whenever my sound stops working in enemy territory, i do the same thing and it generally helps.
other than that, try opening up the sound mixer, and under the menus change the device to check the volumes on all the different "devices".

---

### Post by Sarisar on 2006-09-24
So I'm having .. some.. trouble with sound generally but mostly in democracy.

Google videos always gives sound but youtube almost always doesn't.  It doesn't if I have run anything else using sound (like XMMS or amarok).  If I close that program and firefox down and reload firefox it brings the sound out.

So I tried similar things in Democracy but it didn't work.  However I did notice the 'video progress bar' at the bottom of the screen doesn't always work.  Sometimes it's a full blue bar on the right, even though the video plays, and other times it works properly.  The weird thing is EVERY SINGLE TIME the bar doesn't work, neither does sound, and vice versa.

Also I can't play the .flv files with sound if they didn't work in Democracy.

This may be completely unrelated but I've just downloaded a bunch of random videos and holds true every single time so far.  Are other people finding this?

---


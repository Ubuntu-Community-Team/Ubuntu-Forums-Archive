---
title: "Palm anyone"
date: 2008-06-20
forum: General Help
---

### Post by silvagroup on 2008-06-20
Have had a Tungsten E working with Kubuntu and K-Pilot since 5.10 without a hitch.
Recently purchased a Palm Centro, and unfortunately can not get it to sync. K-Pilot crashes at abbrowser every time.
If I remove the sync functions for abbrowser (Calendar) it syncs but nothing except knotes gets synced.
Any help would be great because I want to get back to my Linux desktop, currently I am bifurcated, Kubuntu for my Organizer and syncing and Kubuntu for everything else, and I left Windows for Kubuntu over six years ago, but now I am back.

---

### Post by danbodoh on 2008-06-23
How about trying JPilot?  

sudo apt-get install jpilot

Go to File...Preferences to set everything up before you sync, including the 'Serial Port', which should be 'usb:' (no quotes, but with the colon.

I've written a JPilot plugin that will download photos from the Centro.  It's available at [http://sourceforge.net/projects/picsnvideos](http://sourceforge.net/projects/picsnvideos)

Dan Bodoh

---

### Post by silvagroup on 2008-06-23
I will try that, because what I have right now is not good.
But will J-Pilot sync with Kontact I thought it was setup for Evolution.

---

### Post by danbodoh on 2008-06-23
JPilot has its own GUI; it doesn't load into other tools.  Gnome-Pilot uses Evolution.

Dan Bodoh

---

### Post by silvagroup on 2008-06-25
danbodoh, sorry for the slow reply.
Should I remove kpilot from my system before using J-Pilot?
And thank you for your replies.

---

### Post by danbodoh on 2008-06-25
I've never used kpilot, so I don't know for certain.  if it automatically launches when you press the hotsync button on the palm, you'll have to at least disable it.  JPilot requires that you press the hotsync button in JPilot, and then do the same on the palm.

Dan Bodoh

---

### Post by silvagroup on 2008-06-25
Thanks, I'll just remove it to play it safe.

---


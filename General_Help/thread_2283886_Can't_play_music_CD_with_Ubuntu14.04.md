---
title: "Can't play music CD with Ubuntu14.04"
date: 2015-06-25
forum: General Help
---

### Post by geovino on 2015-06-25
I've haven't had this problem in all the years I've used Ubuntu. In 14.04 it won't recognize a music CD to play. I can play DVDs but not CDs. What am I missing? 

I use VLC and Banshee.

---

### Post by Frogs Hair on 2015-06-25
The installed ubuntu-restricted-extras combined with Rhythm Box works with all the CD's I've tested so far. A missing codec/s could be the problem.

---

### Post by mc4man on 2015-06-25
You haven't mentioned any error message from the players, if there is one please do so.

With an audio cd inserted does the icon appear in the nautilus sidebar?
(location in nautilus for an audio cd  is cdda://sr0/ or sometimes cdda://sr1/, cdda://sr2/ ect. ctrl+l to use location bar
If not do note that dvd drives use different lens for cd's & dvd's so one can work correctly while the may not (dirty or failing/failed


Or not likely as you say dvd media is fine but still ck.

What you should look at  is the device to be used, in 14.04 only /dev/srX, /dev/cdrom, /dev/cdromX or /dev/sgX are used.
So run this, look for the *-cdrom section & note the logical name: shown. (should be 2 listings
```
sudo lshw -c disc
```
If you happen to have an audio cd in at the time it should also say "configuration: ansiversion=5 status=ready"

Then open vlc > Tools > Preferences > Input / Codecs & make sure that the Default optical device matches one of the above

---

### Post by geovino on 2015-06-26
I just tried another CD and it works fine. It could have been that other CD that had the problem. 
This time the disc show on the tool bar and asked what to play it with and I selected Rhythmbox and it playing. :)

Thanks

---


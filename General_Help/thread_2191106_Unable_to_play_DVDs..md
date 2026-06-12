---
title: "Unable to play DVDs."
date: 2013-11-30
forum: General Help
---

### Post by Roasted on 2013-11-30
Ubuntu 12.04
Fully updated
ubuntu-restricted-extras installed
libdvdcss2 installed (via the install-css.sh script)
libdvdread4 installed
rebooted
both VLC and Totem won't pay two rented DVDs I got from a RedBox tonight.

Am I missing something? I thought the big one was libdvdcss... but even with that and everything else I added, no dice. Eh?

---

### Post by mc4man on 2013-12-01
Have you ever played commercial dvds on this particular hardware before?
If not then maybe you you need to set a region code once (only needs to be set once

If you have played them on this machine before then possibly there is structure protection on both (assuming discs are in good condition
Maybe try vlc in 'dvdsimple' mode (Media > Open Disc >  No disc menus as in screen

---

### Post by Roasted on 2013-12-01
DVDRead could not read block 0.

:(

---

### Post by mc4man on 2013-12-01
> **Roasted said:**
> DVDRead could not read block 0.

:(

Assuming this is correct
> Have you ever played commercial dvds on this particular hardware before?

Is vlc trying to use the correct drive ?
With disk in drive run sudo lshw -C disk to check links for drive (player defaults would be /dev/sr0, /dev/cdrom, /dev/dvd

inside your home folder is .dvdcss (hidden folder
Inside should be files, find the ones for the 2 movies, do they show extracted keys for the various titlesets?

Try inserting disc, once settled with no player open delete the .dvdcss folder, then try vlc on disc again

---

### Post by Roasted on 2013-12-01
Yeah - this system works fine with other DVDs and whatnot. Just this one that seems to have the encryption issue. I'm getting the same issue on my desktop, same OS, entirely different hardware. I have two DVD drives in that desktop and both fail with This Is The End but work with Iron Man 3. This was the same thing I saw on the laptop.

---

### Post by mc4man on 2013-12-01
Sounds like structure protection. It's a Sony movie, in the past Sony's sp wasn't that much of an issue, maybe they've changed it up??
Your best bet would be to find the real titleset number of the main movie & start vlc on that.
You can sometimes find that title # online though in this case I don't think the disc is popular enough. 
If you have a standalone dvd player then it' usually easy to find, start the movie & ck. one of the info options

(have to ask - you picked up a dvd, not a blu-ray?

---

### Post by mc4man on 2013-12-01
The other possibility is to use totem-xine which uses a different dvdnav & used to be better at sp titles
It's been gone for a several years now but can still be built in 12.04 (12.04 is the last time it can

If interested can post how, pretty straightforward, just tested in 12.04.3, screen

---

### Post by Roasted on 2013-12-01
So I might have goofed a bit. After a reboot on my desktop, This Is The End would play fine using Totem, but VLC crashed each time. Meanwhile, Iron Man 3 refused to work period. I pulled an ISO of Iron Man 3 and that ISO also failed.

I thought VLC + libdvdcss was the end-all be-all of DVD playback in Linux? I'm kind of surprised that Totem came out on top. Ironically, and semi unrelated, I've had better success with Totem streaming the MJPG URL's of my surveillance cameras better than VLC... go figure?

---


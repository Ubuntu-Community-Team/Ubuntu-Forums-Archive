---
title: "Amarok won't play Zen Vision M files"
date: 2007-01-11
forum: General Help
---

### Post by OrionsGlory on 2007-01-11
First post here, be gentle.

I've got a Creative Zen Vision M that, thanks to the tutorial, is now being recognized by Amarok. I can see what's already on the player and transfer files to it, but whenever I try to play music off of the player, I get the following error in Amarok:

"These media could not be loaded into the playlist:
file://(whatver).mp3"

I also see this getting spit out:

"amarok:           [PlaylistLoader] The following urls were not suitable for the playlist:
amarok:           [PlaylistLoader]      file://(whatever).mp3"

This gives me the impression that it's interpreting the filesystem on the thing incorrectly and thusly trying to play a file that's not there by using the wrong name.

I'm using Amarok 1.4.4 with libmtp 0.1.2 (though I've tried 0.1.0 as well), both compiled from source on Edgy, with Gnome as the desktop.

So, any thoughts?

---

### Post by dcstar on 2007-01-12
> **OrionsGlory said:**
> First post here, be gentle.

I've got a Creative Zen Vision M that, thanks to the tutorial, is now being recognized by Amarok. I can see what's already on the player and transfer files to it, but whenever I try to play music off of the player, I get the following error in Amarok:

"These media could not be loaded into the playlist:
file://(whatver).mp3"

I also see this getting spit out:

"amarok:           [PlaylistLoader] The following urls were not suitable for the playlist:
amarok:           [PlaylistLoader]      file://(whatever).mp3"

This gives me the impression that it's interpreting the filesystem on the thing incorrectly and thusly trying to play a file that's not there by using the wrong name.

I'm using Amarok 1.4.4 with libmtp 0.1.2 (though I've tried 0.1.0 as well), both compiled from source on Edgy, with Gnome as the desktop.

So, any thoughts?

One assumes you can already play MP3 files on your Ubuntu PC?

---

### Post by OrionsGlory on 2007-01-12
Yes, I've had no problem playing mp3s and most other media formats on Ubuntu.

---

### Post by MoonNSunM on 2007-05-24
I'm curious about Amarok not playing MP3's, whether it is all or only some files?  I have 1 mp3 coded at 320 that will not play in Amarok/Ubuntu.  It's source is an NTFS drive.  All other songs are lower bit rates from that drive and play ok.  I have been able to play the offensive mp3 using other mp3 players.  Can you play the mp3's using another player and is the quality of the MP3 a factor?

---

### Post by strabes on 2007-06-11
libxine-extracodecs maybe

---

### Post by Knoia on 2007-06-22
I have an old Zen Micro, and I'm having the same problem. MP3s will play off my harddrive but not from the player. Similarly, my player docks fine, and I can see all my tracks and transfer to and from the player; I just can't play straight from the device. It seems to me that Amarok is interpretting the file system okay, but is having a problem with streaming songs.

Suggestions, anyone?

---

### Post by redsoftretro on 2007-07-30
The Zen vision M uses the MTP protocol to transfer files. Maybe this does not support direct playing off device itself? I don't think it's like a normal USB drive in this respect.

---

### Post by LingLing1337 on 2007-08-31
Sorry for bringing up a dead thread, but where's the tutorial? I have the same problem with my ZVM. In fact, it won't even be recognized by Amarok.

---


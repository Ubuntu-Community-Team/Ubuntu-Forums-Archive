---
title: "Invalid or incomplete multibyte or wide character"
date: 2007-09-30
forum: General Help
---

### Post by Atypicas on 2007-09-30
Certain torrents seem to fail starting because of a "Invalid or incomplete multibyte or wide character". For example, [this one ]("http://www.mininova.org/tor/728089")does not work because of the error.

The precise error given with this torrent is:

[INDENT]Cannot create /media/sda5/Downloads/BitTorrent/Unfinished/Two Lone Swordsmen/[2004] Fabric 19 [Andrew Weatherall]/03 - M-S Lang??ra (Syntax Erik Mix).mp3: Invalid or incomplete multibyte or wide character[/INDENT]

The fault does not seem to rest with ktorrent as I have tried gnome-btdownload as well and it gave the error. The problem seems to be with the ?? character found in one of the mp3s, but unchecking this still gave the error (as, even if it does not try to download it, it seems to access the information... or something). I imagine that a bittorrent client that completely ignores files that are left unchecked (I'm speaking out of my *** as I have no idea how this all works) might work, but this is just a workaround.

I am curious if there is a setting that I can change that will allow to normally read this invalid character (which is this one: [[SIZE="7"]å[/SIZE]]("http://en.wikipedia.org/wiki/%C3%85")) 

Thank you,

---

### Post by zephyrus17 on 2007-11-23
I am having a similar problem, but involves chinese characters. I have downloaded many language packs, but nothing works. Does anyone know how to fix this?

---

### Post by go_beep_yourself on 2008-01-07
> **zephyrus17 said:**
> I am having a similar problem, but involves chinese characters. I have downloaded many language packs, but nothing works. Does anyone know how to fix this?

I'm having the same problem involving Korean symbols. I found a solution. I could not copy pictures from one partition to another partition on another drive, so I used tar on the directory containing the pictures, and I was able to move the pictures in a tar file afterwards.

---


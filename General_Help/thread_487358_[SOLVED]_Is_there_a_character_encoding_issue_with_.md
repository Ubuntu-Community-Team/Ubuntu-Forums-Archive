---
title: "[SOLVED] Is there a character encoding issue with gtkpod?"
date: 2007-06-29
forum: General Help
---

### Post by ricardisimo on 2007-06-29
I was adding songs to my iPod Nano via gtkpod with minimal troubles, but when I decided to replace all of the high bitrate songs on the player with 128s, I ran into a major problem: none of my songs will show up on the iPod, even though they are clearly saved on the iPod, and gtkpod can see and play them just fine. On the Nano itself - nothing. Just it's normal directory structure ("Albums", "Artists", "Genres" etc.)

The two possibilities that come to mind:
[LIST=1]
[*]I changed the character encoding for tags on gtkpod to Western (ISO-8859-1) instead of "System Charset", which I imagine is UTF-8;
[*]Or, for some reason "Save Changes" works some times but not others - should I be using some other command?
[/LIST]
I have no idea what "Sync Playlist with Directory" does, for example, but perhaps that is the correct way to do things. Or is there some other command I am missing. Thanks in advance for any help.

---

### Post by ricardisimo on 2007-06-29
Resolved... I deleted every song, changed the Character encoding to "UTF-8" in Preferences, and reloaded everything. So, the answer to the question is "yes" - there is an encoding issue either with the Nano or with gtkpod (my guess is the former).

---


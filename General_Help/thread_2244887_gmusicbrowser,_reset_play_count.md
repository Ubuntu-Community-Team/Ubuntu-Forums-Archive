---
title: "gmusicbrowser, reset play count"
date: 2014-09-19
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-09-19
I use a weighted random based on play count and last played, anyway every song has a play count > 100 then i added a few and i don't want it to wear them out by playing them all over and over so i think the easies way would to be rest the play count, anyone know a way to do that?
edit: i just edited ~/.config/gmusicbrowser/gmbrc mnually

---

### Post by ajgreeny on 2014-09-19
Have a look at the gmbrc file in ~/.config/gmusicbrowser and see if a search for the music filename gives any way to edit the count etc etc.

Counts are shown in that file but I've never tried editing it.

---

### Post by Bucky Ball on 2014-09-19
> **pqwoerituytrueiwoq said:**
> 
edit: i just edited ~/.config/gmusicbrowser/gmbrc mnually

@pqwoerituytrueiwoq: This is how you fixed it? Please share your tweak. ;)

---

### Post by pqwoerituytrueiwoq on 2014-09-19
i deleted the songs/album data and let it rebuild it (last 2 sections)

i dont use any really fancy stuff, all i ask form a player is random song from all longs in my music folder, start minimized, and close to tray/icon
stuff like replaygain is useful

i could have just altered the play count from the songs section, but i would have to write a script and parse the data there

---


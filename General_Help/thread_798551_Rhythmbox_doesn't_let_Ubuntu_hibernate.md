---
title: "Rhythmbox doesn't let Ubuntu hibernate?"
date: 2008-05-18
forum: General Help
---

### Post by Tarvok on 2008-05-18
Ever since I upgraded to Hardy, my computer no longer hibernates if I have Rhythmbox open. It did hibernate under Gutsy. The only reason this is a problem is because I used to use that as a "sleep" function, starting something playing, and setting Gutsy to hibernate at some point in time where the music would go from being soothing to being annoying.

For sheer curiosity's sake, anybody have an idea why this is happening? Also, as much as I love Rhythmbox for most purposes, is there perhaps another music program which has this "sleep" function built in, that also won't prevent the computer from hibernating after a while? (This computer, like all computers, runs kind of warm, and I'd prefer it not run while I'm trying to sleep.)

EDIT: Note to self: attempt to solve problem before asking questions. I just snooped around in preferences and plugins, and discovered that there is actually a feature that prevents Ubuntu from sleeping while it's playing. Mind you, it's kind of broken, since it also prevents Ubuntu when it's not playing (when it's paused due to having finished a list), but there I have it.

---

### Post by chrisccoulson on 2008-05-18
Edit: Just noticed its already solved!

---

### Post by lessthanjake on 2008-05-18
There is a plugin "causing" this. It can be en/disabled in gconf-editor. Look under />apps>rhythmbox>plugins>power-manager

---


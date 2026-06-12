---
title: "Messed up Terminal characters in nethack"
date: 2008-03-27
forum: General Help
---

### Post by mordi05 on 2008-03-27
Hi. I'm not really sure where to post this as it could be a nethack problem or a problem with my Terminal.

I've played nethack for a few days in tile mode on my ubuntu distribution. It works fine. However, now I want to play it in my terminal without tiles.

Problem is when I launch the game, the game text is all messed up with strange characters. The map part is displaying ok, i.e. my player and the dungeon, but not the in-game text.

**picture of the problem:**  

[IMG]http://i32.tinypic.com/if25u8.png[/IMG]

**picture of the options menu in game: ** 

[IMG]http://i31.tinypic.com/23jqqmh.png[/IMG]

**picture of my .nethackrc file: ** 

[IMG]http://i29.tinypic.com/4retqg.png[/IMG]

I'm not really sure if this is a nethack problem or a Terminal problem, but the terminal is working fine when not running the game, and the game works fine in tile mode.

My character encoding in the terminal is the usual UTF-8, but I think the game changes it for some reason.
If anyone have any ideas as to what may fix this I'll try it.

Oh, but please don't link me to GNOME NetHack. I know it exists, but I need this to work.

**EDIT:** I have now tried to run it in xterm and KDE Konsole as well as in the initial Terminal (gnome). In Konsole it seems to work, not in the two others.
So this is definitely not a problem with the game. What could be causing this behaviour?

---

### Post by phrawzty on 2008-03-27
> **mordi05 said:**
> **EDIT:** I have now tried to run it in xterm and KDE Konsole as well as in the initial Terminal (gnome). In Konsole it seems to work, not in the two others.
So this is definitely not a problem with the game. What could be causing this behaviour?

Have you tried dropping to the shell entirely to play (i.e. exiting X) ?

---


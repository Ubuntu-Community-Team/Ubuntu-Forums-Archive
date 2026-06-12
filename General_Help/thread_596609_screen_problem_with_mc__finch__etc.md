---
title: "screen problem with mc / finch / etc"
date: 2007-10-29
forum: General Help
---

### Post by freeballer on 2007-10-29
I want to use screen to login to my server from work. I typically open a irssi or finch window, sometimes a mc or nzb/torrent window for downloading. When I use screen with irssi it's fine, when I use it with finch or mc I get a^ (the arrow "^" is suppost to be overtop "a") and/or line distortions (eg. lines are extended beyond the screen width and continue on next line).

So I have two questions;
a) can i use a single screen command to open irssi/mc and possibly other programs and have them named for easier sorting?
b) can screen look more like my bash prompt on programs so the weirdness I described above is eliminated? (ps. if doesn't make sense can send picture later -- at work)

---

### Post by mannih2001 on 2007-10-31
> **freeballer said:**
> 
a) can i use a single screen command to open irssi/mc and possibly other programs and have them named for easier sorting?

That doesn't seem to be possible (but I maybe completely wrong here). As a workaround, you can run screen, set things up the way you like them, and at the end of the session, you don't exit screen but simply detach from the session with Ctrl-a d.

The next time you login, you run screen with the -R option: screen -R and you should be back in your old session.

---


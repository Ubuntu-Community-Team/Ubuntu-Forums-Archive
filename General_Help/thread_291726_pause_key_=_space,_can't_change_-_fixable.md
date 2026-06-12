---
title: "pause key = space, can't change - fixable?"
date: 2006-11-02
forum: General Help
---

### Post by hotani on 2006-11-02
My pause key is somehow mapped to 'space' and I haven't found a way to change it. I tried setting it to 'play/pause' but it keeps showing up as "space". Sometimes when trying to map it to something, if I'm lucky, it will steal the space function so my spacebar doesn't work at all! ](*,)

---

### Post by chriscando on 2006-11-02
Look into the program xmodmap, use that with xev to remap keycodes. Sorry cant explain more now.

---

### Post by hotani on 2006-11-02
well, strange as it is, it seems to be working ok now. But this has happened in the past when I've tried to map something to that key. I'm going to just "back away" now and be happy that it is working!

---

### Post by chriscando on 2006-11-03
If it aint broke...

---

### Post by hotani on 2006-11-04
Figured out the cause of all the trouble: my ATI remote configuration.

I had the 'pause' button on that set to be 'space' since that is what most video players use, unfortunately the pause key on the remote is the same keycode as the pause key on the keyboard. So... when '110' was set to 'space' it made the pause key become space. That is not when the problem started though. When I mapped the 'pause' key on the keyboard to play/pause the music, that is when the spacebar stopped working. ever since then it has been a battle to have a fully functional keyboard and remote. 

Even now my '0' on the keyboard is mapped to return... oops. This is reeeeally bad stuff to me mucking around with, but unavoidable if you have a remote. Ugh.

---


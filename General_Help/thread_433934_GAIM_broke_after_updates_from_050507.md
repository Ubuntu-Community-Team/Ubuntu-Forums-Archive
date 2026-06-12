---
title: "GAIM broke after updates from 05/05/07"
date: 2007-05-05
forum: General Help
---

### Post by Ateo on 2007-05-05
These packages were updated yesterday and one of them broke GAIM. These updates were applied May 5, 2007.

----- May 5, 2007 -----

app-install-data (0.3.30) to 0.3.31
gnome-app-install (0.3.30) to 0.3.31
python (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3
python-minimal (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3

------------------------------

I realize GAIM is on the way out to be replace with Pidgin but am I the only one with this breakage? 

Thanks

---

### Post by neouser99 on 2007-05-05
i don't really see how, i don't believe gaim has any of those dependencies. the only one that i see is python, but i think even then gaim uses it sparingly, and only for custom stuff.

was there some other update that happened, config change, anything?

-neo

---

### Post by Ateo on 2007-05-05
Nope. Nothing. I did my updates in the morning (yesterday), worked all day without issues. Then, at night's end, I shut down. Then booted this morning only to find GAIM dead. The only changes made were the updates. No configs were touched. My desktop is my 'expendible' one meaning I don't mind breaking it. But my laptop, it's my life (as I use it for work and one day down can mean lot's of lost $$ for me) so I don't 'toy' with it.

My thoughts were exactly the same about those updates breaking GAIM. But considering that GAIM broke after my updates, what else am I suppose to think? Not saying it's the updates, I am just putting 2 and 2 together and this is my result.

---

### Post by DoktorSeven on 2007-05-05
By "broke GAIM", do you mean it just doesn't start up anymore?

What does it do when you try running it from the terminal?

---

### Post by Ateo on 2007-05-05
Sorry, should have posted my terminal message earlier...

```
dracco@zeke ~ $ gaim
Segmentation fault (core dumped)
dracco@zeke ~ $ 
```

I also need to mention that these updates were May 4, 2007 (yesterday, my time zone). I changed thread title to reflect this. Either way, the updated package names are correct. My bad. It's been a long week.

---

### Post by neouser99 on 2007-05-05
ateo, give [this]("http://ubuntuforums.org/showthread.php?t=362641") a shot... might be a long one, but still worth it

-neo

---

### Post by Ateo on 2007-05-05
> **neouser99 said:**
> ateo, give [this]("http://ubuntuforums.org/showthread.php?t=362641") a shot... might be a long one, but still worth it

-neo

Yea. That *did* work.

Buuuuuuttt.... I upgraded to pidgin... =)

Thanks for the tip about how to reinstall/revert to previous packages.

---

### Post by erealz on 2007-05-08
i confirm the same problem after installing these packages the other night later on when booted up no connection what so ever...?

---


---
title: "fsck every ** boots"
date: 2006-11-15
forum: General Help
---

### Post by Old Pink on 2006-11-15
How can I knock this up from every 30 boots to every 50/100 boots?

I've seen it mentioned on the forum, but can't for the life of me find it using either Google or Forum Search. Loads of my old threads just vanish, too. I think this forum has problems... :rolleyes:

Anyway, I know it's stupidly easy, so come on, how do I do it?

---

### Post by Old Pink on 2006-11-15
:o No answer? I thought this was common knowledge?!

---

### Post by Old Pink on 2006-11-15
[COLOR=Black]Solved![/COLOR][COLOR=Black]

sudo tune2fs -c [/COLOR][COLOR=Black]50 [/COLOR][COLOR=Black]/dev/hd[/COLOR][COLOR=Black]a1

^^ Every 50 boots, writing how to now
[/COLOR][COLOR=Black][/COLOR]

---

### Post by dcstar on 2006-11-15
> **Old Pink said:**
> [COLOR=Black]Solved![/COLOR][COLOR=Black]

sudo tune2fs -c [/COLOR][COLOR=Black]50 [/COLOR][COLOR=Black]/dev/hd[/COLOR][COLOR=Black]a1

^^ Every 50 boots, writing how to now
[/COLOR][COLOR=Black][/COLOR]

If you do a search for tune2fs in the "Tips and Tricks" forum you should get multiple posts explaining this, there is not much need for yet another duplicating HOWTO.

---


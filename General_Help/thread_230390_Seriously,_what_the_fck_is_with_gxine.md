---
title: "Seriously, what the f*ck is with gxine?"
date: 2006-08-05
forum: General Help
---

### Post by Roasted on 2006-08-05
I went to this web site to watch the trailer of Walk The Line.

[http://www.apple.com/trailers/fox/walk_the_line/medium.html](http://www.apple.com/trailers/fox/walk_the_line/medium.html)

gxine pops up and a porno plays.

What in the f*cking hell?

---

### Post by Tomosaur on 2006-08-05
Strange, works fine for me. Can you repeat the problem? Perhaps someone had been watching some porn and it stayed in gxine's cache or something?

---

### Post by taurus on 2006-08-05
Maybe you want to use mplayerplug-in for your media player instead!!!  You can use Automatix to install it...

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by Roasted on 2006-08-05
K well, I found out why the porno came up. I went to file - playlist and I had a bunch there. At the very bottom was the real trailer I wanted to watch. I deleted them all. Now when I hit play, I just get nothing. Just gotta figure out how to get the preview now. 

That'd kind of suck...

gf "Hey lets go see a movie."

 - "Okay sounds good"

gf "Can you find the preview online first?" 

 - "Sure can."

OHHH AHHHHHHHH HARDERRRRRRRRR

..................[-X

---

### Post by Roasted on 2006-08-05
I TRIED. I just installed mplayer AGAIN but gxine is still used. What am I doing wrong?

---

### Post by Tomosaur on 2006-08-05
I personally dislike gxine - in fact I just installed it now to test your problem out. I find it clunky and generally horrible to use, so my personal reccommendation is to get rid of it :/

---

### Post by Roasted on 2006-08-05
Okay. How?

---

### Post by Tomosaur on 2006-08-05
Open up a terminal and type the following command:

```

sudo aptitude purge gxine

```

---

### Post by Roasted on 2006-08-05
Do I always use that command to get rid of something?

Say I wanted to get rid of wine, would I go sudo aptitude purge wine? Or is the purge command only used for plugins/players?

---

### Post by Tomosaur on 2006-08-05
the purge command removes files other than the program you wish to uninstall.  When I installed gxine earlier, it also downloaded a dependency which I therefore knew I didn't need once gxine was removed. You can use
```

sudo aptitude remove <program>

```

if you're unsure as to what you're removing.

---

### Post by kerry_s on 2006-08-05
Ah man now i feel cheated, i didn't get no porno. You must have got the bonus feature. LOL- just joking of course

---

### Post by Roasted on 2006-08-05
So let's say I wanted to get rid of a program from head to toe, and all files associated with it. Say GAIM for example.

I'd do:

sudo aptitude purge gaim (to get rid of any additional files)

and

sudo apt-get remove gaim (to remove the actual program)

Does "remove" actually uninstall it? Or just delete it? I think I removed Azureus, yet Azureus was still my default torrent client...

---

### Post by Jagot on 2006-08-05
Remove uninstalls the application.  I would personally remove the purge.

---

### Post by Roasted on 2006-08-05
Soooo it's 2 commands I'd do to COMPLETELY get this sh*t out.

purge gxine + remove gxine. Right?


Also - Why is it that when I'm on Apple's web site looking at trailers, each trailer is pretty quiet as far as volume goes. ([www.apple.com/trailers](www.apple.com/trailers))

---

### Post by Roasted on 2006-08-06
.........Am I right? Two commands?

---

### Post by ba5e on 2006-08-06
damn webpage, It crashed my Firefox!!!!

---


---
title: "Childsplay crashing after update."
date: 2006-11-08
forum: General Help
---

### Post by diesel1 on 2006-11-08
Hi all,

I hope someone can help me because my young daughter is very upset about not being able to play her favourite game, Childsplay.

I updated edgy through the normal update mechanism, I think it upgraded the kernel and the glx modules.

I click to start the game and the initial window opens and the cow moos a few times then when it tries to switch to fullscreen  the xserver crashes.

Any pointers would be welcome.

Diesel1.

---

### Post by PriceChild on 2006-11-08
Could you open it from a terminal, reproduce the error and give us the messages displayed in the terminal please.

---

### Post by diesel1 on 2006-11-08
I tried froma terminal but the x server goes down and the terminal obviously goes with it! :)

Diesel1.

---

### Post by diesel1 on 2006-11-11
Hey guys 'n' Gals this is getting serious, I need this program working or it will mean switching to OpenSuse!

Please help.

Diesel1.

BTW I am running Beryl/AIGlx/NVBeta but my other login isn't and also crashes.

OK, I upgraded X, nVidia and beryl and now it works again!

---

### Post by bobromeo on 2007-02-14
It didn't run on my computer either.
I had a schell-script called ´childsplay´ in /usr/bin which was calling .py like this:

/usr/local/lib/games/childsplay/childsplay.py $* &

but there's another shellscript in /usr/games which does this
exec /usr/share/childsplay/childsplay.py "$@"

so I renamed the one in /usr/bin to childsplay.not and now it's not working via terminal, but it does via the menu ;-)

---


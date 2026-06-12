---
title: "Compiling Audio Drivers"
date: 2007-08-25
forum: General Help
---

### Post by karl_eller on 2007-08-25
Alrighty, I'm pretty n00b at Ubuntu and Linux in general, and I want to install the drivers for my ASUS P5N-SLI motherboard. I went to the Asus website, and downloaded the source code... except I really don't know how to compile it :p

So can somebody give me a brief rundown as to what I need to do to turn a .zip file full of source code into something that does stuff?

Cheers

Eller

---

### Post by dragonwings on 2007-08-25
you may not need that zip file try the below first before you open that can of worms

sudo asoundconf list
to get a list of soundcards you have ,take note of them

now
sudo asoundconf set-default-card (here is where you put your sound card name)


eg" for mine i put
sudo asoundconf set-default-card Audigy2

Note if you still have no sound go through check all mutes

good luck hope this helps

---

### Post by karl_eller on 2007-08-25
The sound is working as it is, I just want to install the latest drivers... well because I can, really :p Maybe I'm doing things the somewhat hard way, but I may as well learn now.

Eller

---


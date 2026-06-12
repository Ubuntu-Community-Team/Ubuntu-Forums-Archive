---
title: "Musepack Perdition"
date: 2007-01-29
forum: General Help
---

### Post by matthewstory on 2007-01-29
I've got a bunch of Musepack (mpc) audio files on my linux box, and they work just fine with VLC and TOTEM and mplayer and all that . . . but i'm trying to get everything onto my mac now . . . and iTunes has a problem with mpc files.    I have VLC on my mac, and that plays mpcs just fine, but the whole point is to condense my music libraries.  So . . . i looked around for mpc utils for my Mac, downloaded and installed mppdec, and everytime I run it it produces a 38 MB file, that works, but god it's 38 MB.  So I'm turning to linux.  I need a transcoder that transcodes from mpc to mp3 preferably, but if i can get from mpc to raw or ogg or wav or aiff i can get the rest of the way on my mac with Switch.  Thanks.

---

### Post by matthewstory on 2007-01-29
sweet merciful god.  Ok, i've got this problem solved but it was brutal.  Brutal is a word that I thought I would never have to use again when speaking about Linux . . . but this was Brutal . . . this makes updating to a custom built kernel from source look like a day at the beach.

While waiting for a response I went out looking from programs to do this . . . and unfortunately I found one: Perl Audio Converter (pacpl).  Wow . . . installing this bad boy took me about 2 hours, which is impressive, well worth it though, because this destroys any other converter on the market out of the water . . . this bad boy converts from anything to anything, and so it was worth configuring CPAN and hand resolving oodles and oodles of dependencies . . . and then stracing it untill i had all the other dependancies that it didn't mention installed as well.

HowTO forthcoming.

---


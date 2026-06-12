---
title: "mp3's only play in mplayer all of a sudden"
date: 2006-10-23
forum: General Help
---

### Post by nbound on 2006-10-23
totem says no codec

gxine says demxuer not found


i havent installed/removed any packages recently

i tried reinstalling all my codec packages (and then some), and also checking to see if they were on the list of codecs needed in the restricted codecs part of ubuntu wiki


HELP! ](*,)

---

### Post by Snargle on 2006-10-26
same problem!

except gxine gives no error, just does nothing.
gmplayer says no codec but still plays.
mplayer works fine.
rhythmbox:** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

codecs installed using automatix.

edit: forgot to mention this, it's on an IBM thinkpad T30.

---

### Post by nbound on 2006-10-26
Yep nothing works in VLC or xine either :(

---

### Post by beccon on 2006-10-27
I guess it happened when I run adept to update something like qt... That was the only package to be updated last time I checked before mp3 silenced. I can't use amarok, kaboodle nor noatun - I can use xmms though - but of course this is not a solution.

Any ideas? I reinstalled codecs, even kdemultimedia. What's wrong?? Incompatibilities?


Conrad

---

### Post by Snargle on 2006-10-29
[SIZE="6"][COLOR="Green"]FIXED![/COLOR][/SIZE]

by installing libxine-extracodecs
I think it's in main repositories.

found solution in kubuntu forums, specifically [here]("http://kubuntuforums.net/forums/index.php?topic=9723.0").

:-D :-D :-D :D :) :neutral:

---

### Post by nbound on 2006-10-29
that was already installed on mine... i fixed my by updating (and reformatting) with edgy :P

---


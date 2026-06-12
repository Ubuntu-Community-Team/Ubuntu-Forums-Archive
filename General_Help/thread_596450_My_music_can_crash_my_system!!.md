---
title: "My music can crash my system!?!"
date: 2007-10-29
forum: General Help
---

### Post by Arenlor on 2007-10-29
For some reason if I play my music loudly it crashes my system, the louder it gets the worst my system gets, and when it switches from a quiet part to a loud part it'll freeze up the whole system temporarily, I'm using Rhythmbox on Gutsy, and I've noticed that a couple other things drain my system too, for example running themanaworld or Widelands runs it straight up, using 100% of my 1.8Ghz no matter what. Any idea how I can test my system or anything like that to get a log of what's causing this effect?

---

### Post by Crafty Kisses on 2007-10-29
> **Arenlor said:**
> For some reason if I play my music loudly it crashes my system, the louder it gets the worst my system gets, and when it switches from a quiet part to a loud part it'll freeze up the whole system temporarily, I'm using Rhythmbox on Gutsy, and I've noticed that a couple other things drain my system too, for example running themanaworld or Widelands runs it straight up, using 100% of my 1.8Ghz no matter what. Any idea how I can test my system or anything like that to get a log of what's causing this effect?

Hmmm, see if anything is using resources do the following:
```
top
```
See if anything is taking up a lot of resources.

---

### Post by Arenlor on 2007-10-29
Firefox does, but I normally don't run that and Rhythmbox at the same time, XGL is but I have the cube on so that's probably why, ntos_wq/0 by root is taking up a large amount too, but I have no clue what that is. Those are my top three, Rhythmbox usually falls right in with where firefox is (about third or fourth down the list)

---

### Post by Crafty Kisses on 2007-10-29
> **Arenlor said:**
> Firefox does, but I normally don't run that and Rhythmbox at the same time, XGL is but I have the cube on so that's probably why, ntos_wq/0 by root is taking up a large amount too, but I have no clue what that is. Those are my top three, Rhythmbox usually falls right in with where firefox is (about third or fourth down the list)

Hmmm, weird try disabling XGL.

---

### Post by Arenlor on 2007-10-29
How do I go about doing that?

---


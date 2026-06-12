---
title: "Keyboard issues"
date: 2019-01-21
forum: General Help
---

### Post by teleputer on 2019-01-21
When I press 2 keys at the same time, either 1 hits and the other one is delayed, or the other one does not even register

---

### Post by guiverc on 2019-01-22
I know little about keyboards, but they differ.  My limited knowledge is ..

PS2 keyboards are still made & preferred by some (gamers I'm told), because all keystrokes make it to the machine, which includes all combinations.

USB keyboards on the other hand provide less information which is specific to the keyboard itself (ie. how it interprets the keys pressed and what signal it sends to the machine, ie. this is outside of Ubuntu's control).

I'd suggest using `xev` to explore what your machine see's when you press keys, though you'll likely find whichever is pressed first (it'll likely be only chance that both were pressed at the same time, one usually being a tiny fraction of a second earlier which will impact USB keyboards more than PS2).

---


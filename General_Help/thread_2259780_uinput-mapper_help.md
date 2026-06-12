---
title: "uinput-mapper help"
date: 2015-01-07
forum: General Help
---

### Post by Ovadex on 2015-01-07
I need to take 2 input devices event8 and event9 and output them to a single device js2

I've tried 

./input-read -D -G /dev/input/event9 -D -G /dev/input/event8 | ./input-create

which works except it creates a js device for each event device. I would like to merge them.

Any ideas?

---


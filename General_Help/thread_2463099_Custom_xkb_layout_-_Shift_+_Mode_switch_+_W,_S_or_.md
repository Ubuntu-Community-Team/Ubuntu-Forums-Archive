---
title: "Custom xkb layout - Shift + Mode_switch + W, S or X has no effect"
date: 2021-06-03
forum: General Help
---

### Post by bradleyharden on 2021-06-03
Hi,

I'm using a custom xkb layout file ([here]("https://gist.github.com/bradleyharden/833c8e400f492cb0dda1e041f9d3b5c0")). I don't know much about xkb, but I managed to get it to work. I set it with

```
setxkbmap -layout
```

The layout maps Caps Lock to Mode_switch, and it maps Mode_switch + letters to Greek letters, both lowercase and uppercase. Everything seems to work correctly, except for the specific key combinations of Shift + Mode_switch + W, S or X. For some reason, those particular combinations produce no output. Mode_switch + W works, and Shift + W works, but using all three doesn't work.

I tried it with two different keyboards, so I don't think that's the problem. (Although they are both Dell keyboards, so that may not completely rule it out)

Does anyone have any idea what could be wrong?

---

### Post by bradleyharden on 2021-06-09
Turns out it was the keyboard. Two different Dell keyboards had the same problem. I tried a third Dell keyboard, and it worked correctly for S and X, but not for W. I finally tried an HP keyboard, and it worked without any issues. It must be some common defect with Dell keyboards. I found [this]("https://www.dell.com/community/Inspiron/Inspiron-7577-Caps-Lock-2-w-s-x-randomly-stop-working/td-p/7191409") thread, so that makes sense.

Lesson learned. Don't use random keyboards found in the office junk drawers.

---


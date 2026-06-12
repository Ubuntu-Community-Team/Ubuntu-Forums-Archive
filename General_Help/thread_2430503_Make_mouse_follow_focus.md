---
title: "Make mouse follow focus"
date: 2019-11-02
forum: General Help
---

### Post by vivek1612 on 2019-11-02
On Ubuntu 18.04, is there a way to make the mouse cursor follow the focused window? Specifically, when I alt-tab to windows on different monitors, I would like the mouse cursor to be in the focused window, instead of me having to drag it over there.

I know about [this]("https://askubuntu.com/questions/862254/how-to-move-the-mouse-cursor-between-monitors-with-keys-in-gnome3/1056081"), which works for me, but I was wondering if this can be automated further.

Thanks for the help.

---

### Post by Holger_Gehrke on 2019-11-03
```

xdotool search . behave %@ focus mousemove --window %1 30 20

```
will wait for the focus to change and move the mouse cursor to 30 pixels right and 20 pixels down from the top left corner of the window that just got the focus. The problem with this: it sets up a list of windows that are watched for focus-change. Any windows opened after xdotool has started running will not be on that list. A window that is on that list and gets closed will make xdotool abort with an error. So this obviously needs some more work ...

Holger

---


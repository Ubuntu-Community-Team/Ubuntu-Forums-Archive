---
title: "Monitoring my daily computer use?"
date: 2013-11-30
forum: General Help
---

### Post by AussieGuy on 2013-11-30
In order to find out how much time I'm wasting, I'd like to monitor my usage over time.  My computer is always on, and quite often running a program in the background (I started a program last week that I've calculated that if I let it run until it finishes, it will take over 7700 years). So I need to monitor when I'm actually using it: so when there are keystrokes, mouse events etc.  It would be nice to have software clever enough not to record such things as bumps which might cause the mouse to move, or when the cat walks across the keyboard.  I suppose I could simply download a keylogger, except that I'm not so much interested in what keys I'm pressing, but the times over which I do it.  Same for mouse events.  Ideally I'd like to be able to generate a report, say after a 24 hour period, which tells me the times I was using the computer.

What would be the best software for this kind of personal usage monitoring?

---

### Post by tgalati4 on 2013-11-30
Open a terminal:

```
sudo apt-get install gnotime
gnotime
```

---


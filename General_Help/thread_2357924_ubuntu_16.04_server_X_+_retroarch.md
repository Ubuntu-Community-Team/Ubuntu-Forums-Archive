---
title: "ubuntu 16.04 server X + retroarch"
date: 2017-04-07
forum: General Help
---

### Post by moooartin on 2017-04-07
Hi there,

I've installed ubuntu 16.04 minimal without any DE nor DM.

From the virtual terminal i start a X server with simply a xterm window
From that xterm window, I launch retroarch everything goes fine.
When I leave retroarch and go back to the xterm window the keyboard 'is not working'. 

CTRL+ALT+BACKSPACE (terminate x session) and CTRL+ALT+F1..2... (change virtual terminal) still works

when I try to debug a bit inside this session:*before launching retroarch:*
**xev** detects the keyboard
**evtest** detects the keyboard

*after launching retroarch:*
**xev** does not detect the keyboard
**evtest** detects the keyboard

I dunno what to do, and where to go?
Ho to get my keyboard back after retroarch?

Thank you guys!

---


---
title: "[SOLVED] Recent Gedit slowdowns in Gutsy"
date: 2008-03-05
forum: General Help
---

### Post by Curtisc on 2008-03-05
My apologies if there is a thread about this already, but it's very difficult to search for anything related to gedit in these forums.

I've got Gutsy running on two machines (P4 desktop and centrino laptop), and recently gedit started being very slow on both.  Not only is it slow to load (~10 seconds) but opening dialogues such as preferences or the "find" window takes 6-8 seconds.  This is especially annoying because if I hit "Ctrl-F" and then start typing the word I'm trying to find, it inserts my keystrokes at the cursor in the file instead.

I tried disabling all plugins with no improvement.  Since this happened recently on two machines at once, I'm wondering if anyone else has the same problem.  Perhaps an update did something?

---

### Post by Curtisc on 2008-04-01
Okay, I'm going to mark this solved and explain what the problem is just in case anyone else stumbles across it.  After putting up with Gedit's lagginess for a couple of weeks, it finally dawned on me that it might be an appearance preference that caused the problem (since I'm using the same theme on both computers). Turns out it was my icon theme - "Elementary Icons Small".  I have no idea why the icon theme had such an effect on gedit, but switching to pretty much any other theme gets rid of my issues entirely.

---


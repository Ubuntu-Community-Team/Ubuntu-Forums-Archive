---
title: "Remote SSH session freezes when outputing many lines or ncurses app"
date: 2013-07-17
forum: General Help
---

### Post by xenomuta on 2013-07-17
Hi all, I've been trying to solve the weirdest bug I've ever run into.

I have an ubuntu server 12.04.1 LTS, running kernel3.2.0-49-generic, x86_64.  When I am in a remote SSH shell and I output more than 5 lines or open an ncurses capable app, the terminal completely freezes.
If I open another terminal, the server is still running, all good.
I know it is not a network issue, because I can open two terminals and it only happens in the one I run the ncurses app ( like top, vim, etc... ).

Really have no way to tell whats wrong. Don't really want ot go as far as  stracing and gdbing...

---


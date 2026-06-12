---
title: "[SOLVED]SH script custom ending (14.04)"
date: 2014-04-01
forum: General Help
---

### Post by akarawx2 on 2014-04-01
So I'm trying to make an extension in chrome run a .sh file which it runs fine but the problem is it adds a link but the .sh file runs before the link gets inserted, such as script runs peerflix, but it doesn't add the url before running the peerflix command is there any way to make the sh file "see" the url and add it automatically?


SOLVED: Using the directory for xterm I added  -e peerflix and now it launches my app with the link I needed! so my command was /usr/bin/x-terminal-emulator -e peerflix which loaded my magnet links in peerflix works great.

---

### Post by Mastack on 2014-12-27
Can you share the extension?

---


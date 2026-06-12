---
title: "Accidentally printing from STDIN???"
date: 2008-03-19
forum: General Help
---

### Post by oaul on 2008-03-19
I use the emacs-style cursor navigation in my terminals (ie Ctrl/Alt + (p,n,b,f,etc.)). Sometimes I must accidentally hit a wrong shortcut because i get absolutely random print jobs sent to my printer when im using the terminal. According to cups, these Name of these jobs are all "stdin". It really sucks because when this happens i get like 100+ jobs sent to my printer. This happens frequently enough that it's a pain in the ***, but infrequently enough that i never know what keys i hit when it happens. Anyone know what I'm doing? I use mainly xterm and Eterm. 

-This problem never happens when i leave the box on and unattended overnight or during the day. Only when im typing stuff in an x terminal.
-The 100+ jobs get sent to my printer all at once. Not incrementally.
-My prompt is included randomnly on the actual paper when these jobs print.
-A process shows up when this happens (and hogs 99% cpu). The 'ps aux' owner is user 'lp' and i can't kill it unless i am root, but i can use cups to cancel the job as a normal user. The execution looks somethng like "usb ://<my printer name><lots of crap>" when shown by 'ps aux'

Any help would be greatly appretiated.

---

### Post by oaul on 2008-03-20
**bump**

---


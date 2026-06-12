---
title: "ANSI color change sequences stopped working after upgrade xenial=&gt;bionic"
date: 2020-11-10
forum: General Help
---

### Post by pbwest on 2020-11-10
I have recently upgraded one of two servers from xenial to bionic. I use ssh from my mac to talk to the servers. On bionic, ANSI colour change sequences like ESC[0;33m don't work. The character sequence [COLOR=#ff8c00]ESC[/COLOR][0;33m is displayed instead of the colour changing. (The ESC is displayed with foreground and background reversed.) On xenial, the colours are changed as I expect. In both cases, the TERM is set to xterm-256color. There were some minor changes in the terminfo file, but copying the xterm-256color file across from xenial to bionic made not difference.

The only difference in my stty settings is that iutf8 is set on bionic, and unset on xenial.

I'm completely stumped by this. Any ideas?

---

### Post by pbwest on 2020-11-10
It looks as though the problem is particular to mercurial.  On xenial I had 3.7.?; on bionic, 5.?. When I forced an upgrade of mecurial on xenial, I saw the same problem.

---


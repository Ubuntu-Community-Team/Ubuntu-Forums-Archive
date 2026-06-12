---
title: "How can I get a specific lib file?"
date: 2008-02-23
forum: General Help
---

### Post by RumorsOfWar on 2008-02-23
I'm working on a game that is multi-platform. But when I run the game.bin , I get "error while loading shared libraries: libgtkgl-2.0.so.1: cannot open shared object file: No such file or directory".
I have gtk installed, but this specific lib isn't in the repositories, and if it was I would be worried about it messing with the rest of the system. 
Can I put  libgtkgl-2.0.so.1 in the same directory as game.bin (sort of like a .dll)?  or how would I otherwise handle this?

---

### Post by Lunitik on 2008-02-23
> **RumorsOfWar said:**
> I'm working on a game that is multi-platform. But when I run the game.bin , I get "error while loading shared libraries: libgtkgl-2.0.so.1: cannot open shared object file: No such file or directory".
I have gtk installed, but this specific lib isn't in the repositories, and if it was I would be worried about it messing with the rest of the system. 
Can I put  libgtkgl-2.0.so.1 in the same directory as game.bin (sort of like a .dll)?  or how would I otherwise handle this?

You can use a tool call 'apt-file' for this... just 'sudo apt-get install apt-file' then sudo apt-file update && apt-file search <file>.

Hope this helps.

---

### Post by RumorsOfWar on 2008-02-23
Thanks for the tip, but it didn't seem to find it after 5 min of looking. 
If I can find it, would it hurt to put it in /usr/lib/gtk2.0/modules ?

---


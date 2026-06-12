---
title: "Eterm, Mutt, and Characters"
date: 2008-03-24
forum: General Help
---

### Post by jmfrey on 2008-03-24
I've recently switched to Eterm from Gnome Terminal.  I like the look.

I've downloaded the mutt theme for Eterm and run "Eterm -t mutt" from the launcher.  Standard characters, such as "-" appear as garbage.

However, when I launch an Eterm window and launch mutt from the shell prompt, everything looks fine.

I have the following in my .bashrc: 

export LANG=C

I also have my .bash_profile symlinked to .bashrc.

Any thoughts here?

---

### Post by mssever on 2008-03-26
It may be that eterm -t doesn't launch a shell, so you .bashrc never gets sourced. If you use htop (an awesome next-gen top), you can run it in another terminal and hit F5 to see if mutt is running with bash as its parent.

Another test would be to make a simple wrapper; e.g., ```
#!/bin/bash
export LANG=C
exec mutt
```

Run eterm -t your-wrapper and see if that works.

---


---
title: "[SOLVED] Some links are magic"
date: 2007-09-22
forum: General Help
---

### Post by Kenchu on 2007-09-22
Just wondering about a thing... If I make a link to a script file, lets say the ut2004 script (a game), and place it in /usr/local/bin, and the run the link, it'll whine about missing files and stuff (most likely because it's trying to find the files in the /usr/local/bin folder, I guess, instead of where the actual bin file is). However. When running the installer of this game ut2004, it'll install a link file automatically. This link file (in /usr/local/bin) can be run without any errors. Why is that? And what do link files contain anyway? I seem to be unable to open them or "more" them. Theyll just refer me directly to the "real" file. woot?

---

### Post by kish on 2007-09-22
check out the man page for ln

$man ln

also get some info on the env variables such as PATH.

for better understanding of the magic

check this out.

[http://tille.garrels.be/training/unix/x736.html](http://tille.garrels.be/training/unix/x736.html)

---

### Post by Kenchu on 2007-09-22
Thanks, that explained it.

---


---
title: "terminal wont start inside gnome"
date: 2007-05-23
forum: General Help
---

### Post by plunderisley on 2007-05-23
When I'm logged into the GUI I cant start Terminal. If I ctrl+alt+f2, I can. any way to fix this? It doesnt give me any error message, just tries to load, then cancels out

---

### Post by fanatik on 2007-05-24
does anything start, or is it just terminal that fails?

---

### Post by plunderisley on 2007-05-25
> **fanatik said:**
> does anything start, or is it just terminal that fails?

When I changed my xorg.conf options, got it to work. But had to turn off composite extension, so now I cant use the desktop effects

---

### Post by marlon_za on 2007-07-21
I also have this problem. Appears to be after one installs and configures Nvidia new.
Attempting to start terminal results in "Starting terminal" and nothing else...
Any ideas here yet ?

---

### Post by RubberSideUp on 2007-07-27
This has just started to affect me as well. i turned on nvidia twinview and now i can´t open terminal. Any ideas guys?

EDIT - Does anyone know how i could go about getting into the nvidia settings manager so i could undo whatever it is that i did? i think thats whats broken it.

EDIT #2 - Follow this - [http://ubuntuforums.org/showthread.php?t=511308](http://ubuntuforums.org/showthread.php?t=511308) Big thanks to MrHippocampus for helping with that :) much appreicated.

---

### Post by RAH66 on 2007-09-06
omg got the same problem right now eish gona get me a new card coz nvidia is just giving me crap...

---

### Post by Luke771 on 2007-09-06
Got this problem right after installing... I don't remember what, it was some time ago. I'm now using konsole (I had a lot of kde stuff installed anyway) xterm would also work but I don't like it because it doesn't allow copy-paste.
I had even forgot that I wasn't using gnome-terminal any more, I saw this thread and remembered about it.
Now,iI know that it's not a real solution, but running konsole instead of gnome-terminal works quite fine (use xterm if you don't to install kde  libraries required for konsole)

[edit]
Right, reading all the posts I remembered, it was the nVidia multimonitor thingy.
Well, just run konsole (or xterm).
maybe someone should file a bug about this.

---


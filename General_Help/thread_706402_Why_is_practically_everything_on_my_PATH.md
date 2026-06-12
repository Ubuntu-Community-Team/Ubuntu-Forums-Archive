---
title: "Why is practically everything on my PATH?"
date: 2008-02-24
forum: General Help
---

### Post by Mr. Picklesworth on 2008-02-24
I've realized that effectively every program installed on my computer is located on $PATH. Thus, tab completion for programs cycles through (at most) 3308 possibilities! I find this particularly concerning because of how no real mechanism is in place (aside from trust) to avoid overlapping names. What happens when there are two choices of programs with identical names?

The refactor-hungry side of me says that this is ugly. Is it, or is there an important reason for having applications like Tomboy and Epiphany accessible by their names as opposed to /usr/bin/tomboy?
Stuff in /bin makes sense to me since those commands are frequently referenced in guides and are generally consistent across all systems (whether they are in the same place or not). However, /usr/bin is all non-essential stuff, and having /usr/games under $PATH is simply nonsense.
Possibly a CLI shell could try integrating with the .desktop entry standard to allow easy execution of programs in 'the right way' while trimming down the path.

Maybe I'm missing something, because this seems to have been the way for a very long time.

---

### Post by ssam on 2008-02-24
its pretty much always been like that (of at least the 6ish years i have been using linux).

redhat based systems don't have /sbin or /usr/sbin in the path.

to change it would mean installing the binaries for GUI apps in a different place from command line apps. it would make launching GUI programs from the command line more work.

you should not have to worry about name collisions with apps from the repos. if you ever need to be sure what you are using do
```
which firefox
```
or whatever.

and there are plenty of good command line games (try the bsdgames package, or nethack)

---


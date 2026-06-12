---
title: "unexpected shell behavior"
date: 2007-08-12
forum: General Help
---

### Post by quantumcheese on 2007-08-12
I discovered the following quite by accident.  I was looking at some files in my .Trash directory to decide whether to delete them or not; then, I ran my trash-emptying script from a second terminal.  When I returned to the first terminal, I didn't realize I was in a deleted directory, and I mistyped a command; the below is a recreation of the errors.

```

[mybox ~/.Trash/new]$ what
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-multiverse.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-main.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-restricted.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-universe.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-main.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-multiverse.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-restricted.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-universe.db (2, 'No such file or directory')
bash: what: command not found

```

Does anyone know why the shell seems to look for this command in the repos before erroring out?

---

### Post by tr333 on 2007-08-12
If you attempt to run a program that hasn't yet been installed from the repositories, it will tell you which package to install to get that program.

---

### Post by quantumcheese on 2007-08-14
I've seen that functionality that you mention, but this error is particular to non-existent directories.  Any further thoughts?   It also happened when I typed a non-command such as 's'.

---

### Post by Cryptic1911 on 2007-08-19
I just noticed a similar bug on my computer this evening... (used "what" as an example). I'm on gutsy gibbon which is completely current as of 10 mins ago


$ what
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-universe.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-restricted.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-multiverse.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-main.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-main.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-restricted.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-multiverse.db (22, 'Invalid argument')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/i386-universe.db (22, 'Invalid argument')
bash: what: command not found

---

### Post by quantumcheese on 2007-08-25
Cryptic1911 -- was that in a pre-deleted dir also?  I feel like this is a bug, but not a terribly important one...

---


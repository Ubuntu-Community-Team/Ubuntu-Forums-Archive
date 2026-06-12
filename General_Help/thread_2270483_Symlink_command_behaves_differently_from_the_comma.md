---
title: "Symlink command behaves differently from the command pointed to"
date: 2015-03-23
forum: General Help
---

### Post by tobias-naumann on 2015-03-23
I have tried to play a little bit with Qt and this led to a completely unrelated problem that I am very curious about now: I have a symlink command, which is */usr/bin/qmake*. This symlink points to */usr/bin/qtchooser*. When I run the first I get a different result from running the second. How is that possible?

This is how it looks like in the terminal:
```

user@computer:/usr/bin$ ls -l qmake
lrwxrwxrwx 1 root root 9 Jan 14 22:30 qmake -> qtchooser
user@computer:/usr/bin$ ./qmake
qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory
user@computer:/usr/bin$ ./qtchooser
Usage:
  qtchooser { -l | -list-versions | -print-env }
  qtchooser -run-tool=<tool name> [-qt=<Qt version>] [program arguments]
  <executable name> [-qt=<Qt version>] [program arguments]

Environment variables accepted:
 QTCHOOSER_RUNTOOL  name of the tool to be run (same as the -run-tool argument)
 QT_SELECT          version of Qt to be run (same as the -qt argument)

```

Thanks in advance for every hint.

---

### Post by The Cog on 2015-03-23
I would guess that qtchooser is trying to exec the program name you called it by, in an architecture-specific directory. Not expecting to be called by a different program name.
perhaps something like
```
architecture=$(uname -i)-linux-gnu
/usr/lib/"$architecture"/qt4/bin/$0
```

---


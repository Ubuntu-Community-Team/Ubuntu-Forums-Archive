---
title: "Uh oh...This script line needs help"
date: 2024-10-17
forum: General Help
---

### Post by wyattwhiteeagle on 2024-10-17
It seems as if something in the script line is no longer recognized.
When I run it, nothing happen's except the terminal output.
May I please have help to correct it?

I ran...
```
find /home/wyatt/Downloads/* -type f -iname '*.txt' -print0 | xargs -0 mv --backup=numbered -t /home/wyatt/Desktop/Everything/Text
```
and got...
```
bash: /usr/bin/find: Argument list too long
mv: missing file operand
Try 'mv --help' for more information.
```

---

### Post by Holger_Gehrke on 2024-10-17
Get rid of the asterisk ('*'). You're setting all the files and directories inside ~/Downloads as start point**s** for the search. If that directory is really full, you can exceed the maximum length of a command line (wildcard characters are expanded by the shell, not by the program called unless the wildcard is escaped or quoted; I'm not certain at all if 'find' will handle wildcards in the starting point or if it will assume you mean a directory literally named '*' as the starting point for the search).

Holger

---


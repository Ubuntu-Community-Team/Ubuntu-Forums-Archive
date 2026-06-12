---
title: "question about the &quot;mv&quot; command"
date: 2006-11-26
forum: General Help
---

### Post by neomi on 2006-11-26
when there are two files with the same extension name, eg.(a.txt, b.txt)

if you type mv *.txt in the console, the result will be

like mv a.txt b.txt, as b.txt will be replaced by a.txt with the name "b.txt"

is this a bug or something?

ps.i'm currently using ubuntu 6.10

---

### Post by wastrel on 2006-11-26
This happens because the shell expands your wildcard into a list of the 2 files, so the mv command really looks like 

mv a.txt b.txt

and mv does just that, replaces b.txt with a.txt.  If you had 3 or more text files mv would complain that the destination wasn't a directory.  Anyway, if you think about it, "mv *txt" doesn't make any sense - move them to where?  You should properly have a destination argument for the mv.

If you use the -i flag to mv, it will ask before overwriting files and this problem wouldn't occur.

Hope this helps!

---

### Post by neomi on 2006-11-26
thanks

in fact, i just typed the wrong command so the file suddenly disappeared

an important file...

---

### Post by taurus on 2006-11-26
> **neomi said:**
> thanks

in fact, i just typed the wrong command so the file suddenly disappeared

an important file...
Any change you did the "rm" command!!!

---


---
title: "E:Type '“deb' is not known on line 59 in source list /etc/apt/sources.list"
date: 2016-05-26
forum: General Help
---

### Post by nicolas62 on 2016-05-26
23
I need help with this fail, i have this fail and cant solve, i cant apt-get update, i cant install updates HELP!!!! I'm new in Ubuntu

---

### Post by Bashing-om on 2016-05-26
nicolas62; Hello. Welcome to the forum.

Panic not. Just proceed in a calm and orderly fashion.
A small thing that should be easily resolved.

Let's take a look and see why the system is complaining.
Activate a terminal, and post the results - Between code tags - 
```

cat -n /etc/apt/sources.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And we will advise on making the required edit to the file.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-05-26
Please show us the output in terminal of command ```
cat -n /etc/apt/sources.list
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**
EDIT:
Beaten to it again!

---


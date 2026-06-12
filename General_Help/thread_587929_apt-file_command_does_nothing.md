---
title: "apt-file command does nothing?"
date: 2007-10-23
forum: General Help
---

### Post by loell on 2007-10-23
As some of you might know, **apt-file** is a tool/command to search for a particular file in packages, it is supposed to return the package name where the file belongs to.

but until now, I haven't been able to use it :( , according to tutorials,

you should do

```
sudo apt-file update
```

but it then it does nothing, it seems the program even freezes :(

anybody tried or experienced this?

---

### Post by gmc on 2007-10-23
Just let it run it's course. There's no indiction that it's downloading information from the internet. 

When it's done, you should be good to go with 'apt-file search <filename> | less'

Gord

---

### Post by loell on 2007-10-23
thanks for the tip :)

---


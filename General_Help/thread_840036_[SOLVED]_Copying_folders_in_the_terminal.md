---
title: "[SOLVED] Copying folders in the terminal"
date: 2008-06-25
forum: General Help
---

### Post by solwic on 2008-06-25
I'm trying to copy folders from the terminal, but for some reason am hitting a wall.  Here's what I'm getting:

```
james@ubuntu:~$ cp bin ~/Desktop
cp: omitting directory `bin'

```

Any idea what's up here?  I've changed file permissions and ownership already, and it does this with every single folder.  Files copy fine.  

Is there an option for copying folders that I don't know about?

Thanks!

---

### Post by hydroxic on 2008-06-25
Use the -R flag (recursive)

Assuming bin is the folder you're trying to copy, try this:
```
$ cp -R bin ~/Desktop/
```

---

### Post by solwic on 2008-06-25
> **hydroxic said:**
> Use the -R flag (recursive)

Assuming bin is the folder you're trying to copy, try this:
```
$ cp -R bin ~/Desktop/
```

Dude you're a genius.  Worked like a charm.  Thanks!

---

### Post by iaculallad on 2008-06-25
--Nevermind--

---


---
title: "execute a script without using Terminal"
date: 2006-10-10
forum: General Help
---

### Post by pod25 on 2006-10-10
I'm writing my first python / Tkinter script.
I've got the gui layout done.

Now how do I make my script run without using terminal ? and how do I put a shortcut for it onto my desktop ?

---

### Post by bswilson on 2006-10-10
> **pod25 said:**
> how do I make my script run without using terminal ? and how do I put a shortcut for it onto my desktop ?

You can enter this command to make a desktop shortcut for your script:

```
$ ln -s /path/to/your/script.py /home/yourusername/Desktop/script.py
```

---

### Post by pod25 on 2006-10-10
> **bswilson said:**
> You can enter this command to make a desktop shortcut for your script:

```
$ ln -s /path/to/your/script.py /home/yourusername/Desktop/script.py
```
Thanks.
I made the shortcut and changed the permissions to execute, so now when double clicked it asks to run, which will do for now.

---


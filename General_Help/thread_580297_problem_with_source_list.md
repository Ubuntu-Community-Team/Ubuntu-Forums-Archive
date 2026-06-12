---
title: "problem with source list"
date: 2007-10-18
forum: General Help
---

### Post by Vicfred on 2007-10-18
hi when i try to install something on command line i get this error... what should i do?

```
E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

```

[IMG]http://img515.imageshack.us/img515/2255/errorst1.jpg[/IMG]

---

### Post by Stemp on 2007-10-18
You probably have an error in your /etc/apt/sources.list file, just look at it to find the problem on line 5.
```
gksudo gedit /etc/apt/sources.list
```

If yoy cannot find the error, copy the content here ;)

---

### Post by maddiez on 2008-03-25
hmm...
it seems there could be a bug in the "Software Sources" selector on Hardy

i just did a clean install, and was trying to figure out which server could be faster for me.
after series of tests and changes, the program crashed and i tried apt-get update the message popped up.

and i open up the sources.list, the place where the URL should be has been replaced by a word "United States". hmm... weird?

---

### Post by voku1987 on 2008-05-10
I think you have spelling mistake or so in your source.list... if you want to find some new server for your Ubuntu Hardy -> [www.kkc4u.de]("http://www.kkc4u.de/phpBB3/viewtopic.php?f=504&t=652")

---


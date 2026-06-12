---
title: "error msg in synaptic package manager"
date: 2007-10-04
forum: General Help
---

### Post by bartfliet on 2007-10-04
Hello,

Whenever I try to start "synaptic package manager" or press "add/remove" I keep getting this error message.

```
E: Type '"deb' is not known on line 41 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem,
E:_cache->open() failed, please report
```

Please, what can I do about this?

---

### Post by forestpixie on 2007-10-04
you need to open the file to edit it

```
gksudo gedit /etc/apt/sources.list
```

find line 41 and change the line so it reads right, chances are it starts > "deb that should be > deb

if you're not sure post the file here
do an update after you've edited it

```
sudo apt-get update
```

---


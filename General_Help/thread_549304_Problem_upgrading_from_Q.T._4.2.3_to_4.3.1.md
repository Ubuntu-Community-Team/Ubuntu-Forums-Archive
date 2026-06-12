---
title: "Problem upgrading from Q.T. 4.2.3 to 4.3.1"
date: 2007-09-12
forum: General Help
---

### Post by jmags on 2007-09-12
I installed QT 4.2.3 manually, and subsequently downloaded 4.3.1 and installed it, without taking any uninstall steps. By and large, this seems to have worked. There is a 4.3.1, but not a 4.2.3 folder in /usr/local/Trolltech. However, qmake -version returns 

```

QMake version 2.01a
Using Qt version 4.2.3 in /usr/lib

```

I have edited my paths in .bashrc, and there is no reference to QT in /etc/environment, so I'm at a bit of a loss.

---

### Post by Cyvros on 2007-09-13
Not really helpful at all, but I'm having exactly the same problem, except that I installed Qt first through the repos, then did 4.3.1 manually.

---

### Post by Cyvros on 2007-09-14
I've figured it out, thanks to [this thread](http://ubuntuforums.org/showthread.php?p=3348910). You need to add this:

```
export PATH=/usr/local/Trolltech/Qt-4.3.1/bin:$PATH
```

To your ~/.profile file (rather than /etc/bash.bashrc).

---


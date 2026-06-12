---
title: "help installing wink..."
date: 2008-03-18
forum: General Help
---

### Post by Mia_tech on 2008-03-18
I'm trying to install wink... and I keep getting this error
```
jorge@ubuntu-box:~/wink15$ sudo sh ./installer.sh

Wink requires that the following packages be installed to run properly. Please install them and try again.

libstdc++.so.5

```

I've looked for the libstdc++.so.5 everywhere, and no luck...how could I get the dependencies for this install done?

thanks

---

### Post by Mia_tech on 2008-03-18
here's the solution to the above problem
[http://www.debugmode.com/userforums/viewtopic.php?t=6125&highlight=jorge+ubuntubox+wink15+sudo++installer++wink+requires+following+packages+installed+run+properly+install+try+again+libstdc](http://www.debugmode.com/userforums/viewtopic.php?t=6125&highlight=jorge+ubuntubox+wink15+sudo++installer++wink+requires+following+packages+installed+run+properly+install+try+again+libstdc)

---

### Post by sub2007 on 2008-03-18
I think this should do the trick:

```
sudo apt-get install libstdc++5-3.3-dev
```

EDIT: didn't see the previous poster. Before posting I searched in my repos and it does have libstdc++5. Weird...

---


---
title: "Changing java path"
date: 2006-07-12
forum: General Help
---

### Post by Culito on 2006-07-12
Disclaimer:  I've been drinking rum&cokes.

Alright, I'm trying to install and compile a program so I can communicate with my Arduino board(google it.)  I can get all the way to configuring rxtx - then I get this error:
./configure: line 21245: javac: command not found
checking java.home  Exception in thread "main" java.lang.NoClassDefFoundError: conftest

configure: error: Make sure java is in your path before running configure

So...how do I change the path?  Or add a directory to the path?

For the record...Java has been the bane of my whole Ubuntu experience.  Everything else - awesome!

-C

---

### Post by Jagot on 2006-07-13
You could see if this works:

```
sudo update-alternatives --config javac
```

---

### Post by panurge77 on 2006-07-13
or maybe
```
$JAVA_PATH=/path/to/java/
```

---

### Post by Culito on 2006-07-13
Thanks guys..

Ok, the first options says "no alternatives found".

So...where would I use the $JAVA_PATH line?  @ the command line, in the rxtx directory, (where I'm doing the compiling), pointing to /usr/share/java?

---


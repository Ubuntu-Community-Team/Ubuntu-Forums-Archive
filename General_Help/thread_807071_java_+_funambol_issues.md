---
title: "java + funambol issues"
date: 2008-05-25
forum: General Help
---

### Post by Darth_tater on 2008-05-25
Ok, I recently upgraded my file server to 8.04.  I installed azureus and got every other function working correctly.  My problem is this:  Azureus works perfectly, so I know java is installed, but when I try to launch funambol, I get this error message. 
```

$ /opt/Funambol/tools/bin/funambol.sh: 113: /opt/Funambol/tools/jre-1.5.0/jre/bin/java: not found 

```

I don’t understand why, because there is a java binary inside of that directory.

When I run ‘java –version’ this is the output
```

karl@Cortana:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

```

any ideas as to why funambol isint starting up?

---


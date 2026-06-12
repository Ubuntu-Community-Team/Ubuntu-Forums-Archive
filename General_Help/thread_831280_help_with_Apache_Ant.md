---
title: "help with Apache Ant"
date: 2008-06-16
forum: General Help
---

### Post by IvanIvan on 2008-06-16
why is this happening?

```
ivan@ivan-t60p:~/Bruce Eckel - Thinking in Java 4th ed/TIJ4-Code$ ant
Buildfile: build.xml

run:

build:

BUILD FAILED
/home/ivan/Bruce Eckel - Thinking in Java 4th ed/TIJ4-Code/build.xml:51: The following error occurred while executing this line:
/home/ivan/Bruce Eckel - Thinking in Java 4th ed/TIJ4-Code/object/build.xml:29: J2SE5 required

```

I have installed Java SE 6 JRE & JDK via Synaptic.

---

### Post by IvanIvan on 2008-06-17
anyone?

---

### Post by CSEatOSU on 2008-06-25
post your build.xml so I can see line 29.

---

### Post by James Gregory on 2009-05-08
The build files incorrectly check for Java 1.5 rather than Java 1.5 or greater. If you have Python installed you can fix it with this script:

```
import os
import re

def fix():
    dir = 'C:\Documents and Settings\gregorj\My Documents\TIJ'

    for root, dirs, files in os.walk(dir):
        for name in files:
            fullname = os.path.join(root, name)
            f = open(fullname, 'r')
            text = f.read()
            f.close()
            f = open(fullname, 'w')
            text = re.sub('(?s)\w*<fail message="J2SE5 required" unless="version1.5"/>\n', '', text)
            f.write(text)
            
fix()

```

---


---
title: "Cross Platform Compiler"
date: 2008-06-09
forum: General Help
---

### Post by Carlos Pena on 2008-06-09
I am looking for a good ubuntu-windows-mac object oriented c (or basic) compiler or development software. Could anybody help me?

Carlos Pena
Santo Domingo, Dominican Republic

---

### Post by Rocket2DMn on 2008-06-09
gcc is basically the universal C compiler, however you can't compile binaries that work between the systems.  The closest you get is using Java which compiles classes that are then used by the JVM/JRE on different platforms.
To install gcc and related libraries in Ubuntu, you want the build-essential metapackage
```
sudo apt-get install build-essential
```

---


---
title: "Frostwire hang on start"
date: 2007-08-10
forum: General Help
---

### Post by PWill on 2007-08-10
When I start Frostwire, it says

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct


and then just sits indefinitely.

java -version outputs 
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

I have used update-alternatives to update to the correct version of Java. Anyone?

---

### Post by bwtranch on 2007-08-10
I don't know. Looks like some kind of a bug. I'm not that crazy about Java. Buugy on windoze, seems to be buggy on Linux, too.

---

### Post by BlackAnthrax on 2007-08-12
I've tried Frostwire, it is ok. However, you may find that GTK-Gnuttella (in the repos) works just as well too. Also, just for figuring out what is wrong, see what Limewire does. Limewire has a Linux version, and although an older version (I believe), will help us decide whether the bug is in Frostwire or Java.

---


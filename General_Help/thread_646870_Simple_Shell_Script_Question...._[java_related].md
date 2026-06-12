---
title: "Simple Shell Script Question.... [java related]"
date: 2007-12-21
forum: General Help
---

### Post by Drags111 on 2007-12-21
I have a simple problem for a big program.
We have a .sh to install it, but when I run the .sh in terminal like i should, It says the class is not found. I believe it has to do with the syntax, as the person who made it is not a linux pro. I don't know MUCH about shell scripts, but I'm pretty sure I know where the error lies.

Our Script:
```
java -classpath ./:./jars/tools.jar:./jars/nexus.jar impsoft.nexus.installer.Install

chmod a+x run.sh compile.sh
```

The Error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: impsoft/nexus/installer/Install

```

What I think the problem is:
```
./jars/nexus.jar impsoft.nexus.installer.Install
```

Thank you for ALL of your help!

---

### Post by big_area on 2007-12-21
what is your working directory when you run this script?

---

### Post by Drags111 on 2007-12-21
im in the directory of the shell script. The first part of that works, so im pretty sure it doesnt have to do with the directory.

---


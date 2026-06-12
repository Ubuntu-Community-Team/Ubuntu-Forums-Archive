---
title: "What is the command for opening a jar file?"
date: 2008-05-17
forum: General Help
---

### Post by Tyke91 on 2008-05-17
I'd like to create a menu shortcut for a game that runs in java, but I don't know the terminal command to get it to open.

 using ```
java
``` doesn't seem to work, it can't find the program's main method.

If I right click on the file, I can open it in either OpenJDK or sun java 6 and it will run. But how do I do this in the terminal?

---

### Post by Thanoulis on 2008-05-17
From the OpenJDK Java menu icon:
```
/usr/lib/jvm/java-6-openjdk/bin/javaws %u
```
I believe that you can type that in a terminal also...:)

---

### Post by luisromangz on 2008-05-17
The command to run jar files is 

java -jar

It is explained in man java, of course.

---


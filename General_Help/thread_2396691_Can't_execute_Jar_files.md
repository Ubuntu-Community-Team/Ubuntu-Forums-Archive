---
title: "Can't execute Jar files"
date: 2018-07-19
forum: General Help
---

### Post by Arminius on 2018-07-19
So there's a jar file, I ticked it as "allow executing file as program"
right click has Open with oracle java 8 runtime
but nothing happens when it's executed.

---

### Post by slickymaster on 2018-07-19
What do you get when you run ```
java -jar name_of_jar_file.jar
``` from the command line in the directory the jar file is?

---

### Post by Arminius on 2018-07-19
> **slickymaster said:**
> What do you get when you run ```
java -jar name_of_jar_file.jar
``` from the command line in the directory the jar file is?
input
```
user@computer:~/Downloads$ java -jar name_of_jar_file.jar
```
output
```
no main manifest attribute, in name_of_jar_file.jar
```

---

### Post by slickymaster on 2018-07-19
You have to replace **name_of_jar_file.jar** in the example with the actual name of the jar file present in your computer

---

### Post by Arminius on 2018-07-19
I did, sorry, whenever I reveal what I'm currently running people usually wonder why I'm running that and not their opinion of what's better.
So I did run the real jar file.

---

### Post by slickymaster on 2018-07-19
> **Arminius said:**
> input
```
user@computer:~/Downloads$ java -jar name_of_jar_file.jar
```
output
```
no main manifest attribute, in name_of_jar_file.jar
```
The **-jar** option only works if the JAR file is an executable JAR file, which means it must have a manifest file with a Main-Class attribute in it. If it's not an executable JAR, then you'll need to run using the **-cp** switches:```
java -cp name_of_jar_file.jar com.somepackage.SomeClass
```

---


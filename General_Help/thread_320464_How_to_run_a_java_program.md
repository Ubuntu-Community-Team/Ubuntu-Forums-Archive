---
title: "How to run a java program?"
date: 2006-12-17
forum: General Help
---

### Post by Daandaan on 2006-12-17
I wanted  to program in linux so I used geany, a fast and ligthweight IDE. I wrote a simple Hello world! program (:mrgreen: ) to test the program. I pressed compile, and I saw appear a .class file, good, then I pressed execute and the message said Failed to execute /home/daan/Hello (Make sure it is already built). But it was already built so I'd try to ran it in a terminal. I did java ./Hello.class    =>   Exception in thread "main" java.lang.NoClassDefFoundError: //Hello/class

There is also another interpreter i saw so i did gij ./Hello.class   =>

Exception in thread "main" java.lang.NoClassDefFoundError: ..Hello.class
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: ..Hello.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

This must be something with a classpath rigth? I totally don't know how a $PATH or something like that works. Would somebody be so kind to tell me how to set the path right so i can execute a java program or just explain me how paths work and what they're needed for :) 


P.s. I think if i could run the program in a terminal I'll also be able to run it in geany.
Thx in advance 
Daan

---

### Post by meng on 2006-12-17
I'm not sure I know the answer, but what if you just try
java Hello.class
without the ./

---

### Post by bettlebrox on 2006-12-17
Try

java Hello

When you do "java Hello.class", java will look for a java program called class in a package named Hello.

---

### Post by Daandaan on 2006-12-18
Hehe, bettlebrox was rigth, it works...in terminal. However I still can't run it in geany.](*,) :-k



EDIT: I changed the "set includes and arguments" for execution to my java path : (/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java). And now I see in a flash "Hello world!" :) but the windows disappears directly, what shoud I do. Does someone know a better IDE, or an editor like Textpad(windows) for linux.??
Greetz Daan

---

### Post by steve.horsley on 2006-12-18
I really like this simple jave ide:
[http://www.bluej.org/](http://www.bluej.org/)

---

### Post by bettlebrox on 2006-12-18
I use Eclipse meself. Eclipse 3.2 is a big improvement over 3.1 (a lot faster and more lightweight). It might be a wee bit more heavyweight than what U want.

---

### Post by raul_ on 2006-12-18
U have to tweak Eclipse to use Java 5 though.Or at least i had to

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Integrated_Development_Environment_.28Eclipse.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Integrated_Development_Environment_.28Eclipse.29")

---


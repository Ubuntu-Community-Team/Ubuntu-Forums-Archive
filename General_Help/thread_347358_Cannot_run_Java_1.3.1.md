---
title: "Cannot run Java 1.3.1"
date: 2007-01-27
forum: General Help
---

### Post by denispyr on 2007-01-27
Hi all.
I recently moved all my stuff to (K)Ubuntu (no dual boots anymore) and I am using Edgy. Now I'm moving my legacy stuff.
I installed Java (JDK 1.3.1.19) but when I'm trying to run it I get "error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory".
Instructions say that I need "Linux kernel v 2.2.12 and glibc v2.1.2-11 or later". I have kernel 2.6.17 and /lib/libc-2.4.so.
Does anybody have a clue on how to proceed?

PS If I can't run Java 1.3.1 I should setup a dual boot machine and keep working on XP](*,) Please help me!!!!

---

### Post by aliyanage on 2007-01-27
Hi,

did you already try installing java using automatix? It's quite a lot easier...
check out this site and follow the instructions to install automatix:

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

than start automatix and simply install java...


regards
aliyanage

---

### Post by denispyr on 2007-01-27
thanks aliyanage but not what I really need. I also have jdk 1.5 and 1.6 and they are working OK. What I need is to install specifically jdk 1.3.1.
thanks for your reply

---

### Post by phossal on 2007-01-30
You download previous releases directly from SUN. Version 1.3.1 is still available. Check it out here: [Java 2 SDK]("http://java.sun.com/j2se/1.3/download.html"). You can follow the instructions in my sig on how to install it. Contact me if you need help.

---

### Post by phossal on 2007-01-30
Okay, so you've downloaded and installed JDK 2 from SUN? And now you're still generating error messages? Post the command you're running, and the error messages.

---

### Post by denispyr on 2007-01-30
-

---

### Post by denispyr on 2007-01-30
denispyr@computer:home/denispyr/jdk/1.3.1/bin~$ ./java
/home/denispyr/jdk/1.3.1/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

---

### Post by phossal on 2007-01-30
Try that again, because I can't understand it. Drop the bash output.

Make your command look like this:
```
command
```

And the errors like this:
```
errors
```

---

### Post by denispyr on 2007-01-30
```
./java
```

```
/home/devtools/jdk/1.3.1/bin/i386/native_threads/java: error while loading shared libraries libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
```

---

### Post by phossal on 2007-01-30
Just out of curiosity, did you install build-essential?
```
sudo apt-get install build-essential
```

Even if you have, run it again.

---

### Post by denispyr on 2007-01-30
yes. Just tried it again and received "build-essential is already the newest version."

---

### Post by phossal on 2007-01-30
```
sudo apt-get install libstdc++6-4.1-dbg
```

---

### Post by denispyr on 2007-01-30
just did it. Nothing changed.

---

### Post by phossal on 2007-01-30
Download this:
```
sudo apt-get install libstdc++2.10-dbg
```

Once installed, make a link:
```
sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2
```

That'll work. If you want to call java from anywhere, you'll need to either set JAVA_HOME manually, or include it in update-alternatives.

I just installed the JDK2 successfully myself to test it. So I know it works.

```
bash 3.1:java
/home/phossal/Desktop/JDK2/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
bash 3.1:java -version
java version "1.3.1_19"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.3.1_19-b03)
Java HotSpot(TM) Client VM (build 1.3.1_19-b03, mixed mode)
bash 3.1:
```

---

### Post by denispyr on 2007-01-30
phossal, that did it! Thanks - you saved me from a dual boot system!

---

### Post by phossal on 2007-01-30
No problem! I'm glad you're up and running. Have a good day/evening. Cheers!

---

### Post by jpaulson on 2007-02-08
```
sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2
```

worked for me too. Thanks

---


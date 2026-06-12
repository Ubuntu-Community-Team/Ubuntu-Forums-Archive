---
title: "jni.h not found while installing R"
date: 2016-12-05
forum: General Help
---

### Post by giacomotb on 2016-12-05
Hello!
I'm installing R and I ended up in the fatal error: ```
configuring Java ...
Java interpreter : /usr/bin/java
Java version     : 1.8.0_111
Java home path   : /usr/lib/jvm/java-8-openjdk-amd64/jre
Java compiler    : not present
Java headers gen.: 
Java archive tool: 

trying to compile and link a JNI progam 
detected JNI cpp flags    : 
detected JNI linker flags : -L$(JAVA_HOME)/lib/amd64/server -ljvm
make[2]: ingresso nella directory "/tmp/Rjavareconf.BZmqAJ"
gcc -I/home/giacomo/R-3.0.2/include -DNDEBUG  -I/usr/local/include    -fpic  -g -O2  -c conftest.c -o conftest.o
conftest.c:1:17: fatal error: jni.h: File o directory non esistente
compilation terminated.
/home/giacomo/R-3.0.2/etc/Makeconf:122: set di istruzioni per l'obiettivo "conftest.o" non riuscito
make[2]: *** [conftest.o] Errore 1
make[2]: uscita dalla directory "/tmp/Rjavareconf.BZmqAJ"
Unable to compile a JNI program




```, in English "No such file or directory". 
I tried to locate with locate jni.h, but this gave me no result.
But actually java ist installed, indeed typing ```
sudo apt-get install default-jre


``` or ```
 sudo apt-get install openjdk-8-jre


``` doesn't install anything new.
How can I solve this problem?

---

### Post by angarita on 2017-11-01
Try: 
# sudo apt-get install openjdk-8-jdk

jre -> java runtime environment (no .h files included)
jdk -> java development kit (.h files included)

---

### Post by oldos2er on 2017-11-01
Old thread closed.

---


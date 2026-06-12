---
title: "Allow java ubuntu 14.04"
date: 2014-09-09
forum: General Help
---

### Post by jotacebusta2 on 2014-09-09
Hi all,

I have a galago from system 76, but I'm having trouble with java. I cannot display 3d-surfaces in the sage notebook. I cannot see applets that I've generated with geogebra neither. Nvertheless, when I try to visualize the surfaces from the command line mode in sage, things go fine, Jmol is there and working. Also Geogebra works properly. Further, when I go to java.com and I try to detect java in my computer, then nothing happes, it's just like the rectangle in which the test should apear is left blank.

I've been playing around, installing, un-installing icedte, the various options of jre, configuring java options, and so on... but things are simplu not working. This is not the first time I have this problem I'm sorry for asking again, but none of the solutions I tried works.

Thanks,

JC

---

### Post by claracc on 2014-09-10
I would try to install oracle java 8 through webup8 ppa repository.

Here you have a link to do so step by step: [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

Also, it can be interesting to read this other link: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by jotacebusta2 on 2014-09-10
Thanks a lot, I tried what is suggested in the first link you give, but nothing has changed. I verfied on the Firefox side, and the plug-in seems to be there, and even it enabled. Any suggestion?

---

### Post by QIII on 2014-09-10
Hello!

Would you please post the results of 

```
java -version
```

---

### Post by jotacebusta2 on 2014-09-10
xxx@yyy:~$ java -version
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-Bit Server VM (build 25.20-b23, mixed mode)

Also, if this can help

xx@yy:~$ sudo update-alternatives --config java
Il existe 3 choix pour l'alternative java (qui fournit /usr/bin/java).

  Sélection   Chemin                                          Priorité  État
------------------------------------------------------------
* 0            /usr/lib/jvm/java-8-oracle/jre/bin/java          1072      mode automatique
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      mode manuel
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      mode manuel
  3            /usr/lib/jvm/java-8-oracle/jre/bin/java          1072      mode manuel

Appuyez sur <Entrée> pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné

---

### Post by QIII on 2014-09-10
Then you have Oracle Java 8 installed and it is the one being used.

Can you tell us more about the other application you are trying to use?

---

### Post by jotacebusta2 on 2014-09-10
So far the problems are detected when I use SAGEmath via the notebook (in firefox). For plotting 3d surfaces it calls Jmol to show an interavtive plot (so one can turn, and so on). The problem does not come from Jmol, since when I plot the same surface but using the command line mode of SAGEmath, everything's fine. The Jmol window pops ud as expected, with my nice surface on it.
On the other hand, applets produced with geogebra are not working.
When I go to java.com and try to test if I have java, nothing happens (this is also the case for chromium).
Something else that might not be related at all : bluefish crashed at the very moment I launch it.

---

### Post by jotacebusta2 on 2014-09-10
By the way, I have anotehr computer, running on Ubuntu 12.04 (old dell, 32 bits). In that one, I have  
xxx@yyy:~$ java -version
java version "1.6.0_32"
OpenJDK Runtime Environment (IcedTea6 1.13.4) (6b32-1.13.4-4ubuntu0.12.04.2)
OpenJDK Server VM (build 23.25-b01, mixed mode)

And everything works just fine. Geogebra also works as it should, and the same holds for the applets.
Should I try to go to OpenJDK?

---

### Post by QIII on 2014-09-10
Not 6, no.  Security issues.

Not sure OpenJDK 7 would help, though.

The relationship between Oracle Java and OpenJDK is this:  Oracle decreed that OpenJDK is the open source reference implementation for all things Java -- for which they hold copyright.

That even applies to Oracle Java.  So Oracle Java is required to comply with the OpenJDK spec.  (Not that Oracle is losing anything:  They are the prime mover in development of OpenJDK.)

What I'm saying is that it's not likely anything will improve.  It is more likely that your software required Java 6 at some point and hasn't been updated to work with Java 7 or 8.

But it is worth a try.  Again, not OpenJDK 6.  Try OpenJDK 7 and see.  It's worth a try.

---


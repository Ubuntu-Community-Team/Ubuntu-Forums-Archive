---
title: "Java help"
date: 2007-03-04
forum: General Help
---

### Post by adarkmethod on 2007-03-04
ok, i used the AddRemove Tool in Ubuntu Edgy 6.10 to install Java 5, yet my azureus is still telling me im using 1.4.2


why? and how do i fix it

---

### Post by Ramses de Norre on 2007-03-04
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by adarkmethod on 2007-03-04
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/serialver
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-snapshot-javaplugin.so'.

---

### Post by Ramses de Norre on 2007-03-04
Don't worry about the "does not exist" stuff, that's because you haven't got the jdk installed and you probably don't need it.
Does azureus use java5 now?

---

### Post by adarkmethod on 2007-03-04
no, it still says im using 1.4.2

this is kinda frustrating, but im sure im jsut doing something retarded

---

### Post by Ramses de Norre on 2007-03-04
What's the output of **java -version**?
Maybe azureus has a config file which specifies the java executable it uses.

---

### Post by adarkmethod on 2007-03-04
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

thats the output

---

### Post by Ramses de Norre on 2007-03-04
You'll have to look in azureus' config files then... I can't help you with that because I don't use azureus myself.

---

### Post by adarkmethod on 2007-03-04
ahh, well thanx anyways

---


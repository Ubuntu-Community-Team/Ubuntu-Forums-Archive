---
title: "Java 1.5, where and how?"
date: 2007-08-31
forum: General Help
---

### Post by Batuhan on 2007-08-31
I need java 1.5 for an application.

java -version spits:

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

Synaptic does not help, what should I do to get java 1.5 working? (with browser plugin of course)

Thanks

---

### Post by testube_babies on 2007-08-31
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Batuhan on 2007-08-31
Actually that link is the exact link for the guide I used to install my current java which is v1.4.
Am I missing something there?

---

### Post by stchman on 2007-08-31
> **Batuhan said:**
> I need java 1.5 for an application.

java -version spits:

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

Synaptic does not help, what should I do to get java 1.5 working? (with browser plugin of course)

Thanks

First uninstall the Java 1.4 and use this to install Java 1.5.

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

This will do it.

---

### Post by testube_babies on 2007-08-31
That should have installed java 6.

Try 'sudo update-alternatives --config java' to see if it installed correctly, and if it did you should be able to choose it as your new default.

---

### Post by Batuhan on 2007-08-31
Thanks!

```
sudo update-alternatives --config java
```

did it.

---


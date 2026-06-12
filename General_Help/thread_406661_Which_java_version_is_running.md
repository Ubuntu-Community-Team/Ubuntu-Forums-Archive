---
title: "Which java version is running?"
date: 2007-04-11
forum: General Help
---

### Post by Franscisco on 2007-04-11
Does anyone know which Java version is running on my computer(ubuntu)?
how can I get rid of that version?

---

### Post by jakev383 on 2007-04-11
> **Franscisco said:**
> Does anyone know which Java version is running on my computer(ubuntu)?
how can I get rid of that version?

```

dpkg -l | grep java

```
To remove I'd suggest using Synaptic (under System -> Administration), or maybe sudo apt-get remove sun-java5-bin or something similar.

---

### Post by Stephen Howard on 2007-04-11
at a console type:
```

java -version
```

Probably remove it with the *apt-get remove *command.

---

### Post by Franscisco on 2007-04-11
I think I have two Java versions installed, and I wish I can uninstall the oldest version? how to so it?

---

### Post by IcemanV9 on 2007-04-11
What makes you say that you think you have two (2) versions of Java installed?? Did you do "java -version" and "dpkg -l |grep java" ??

---

### Post by zvacet on 2007-04-11
You can see all java versions in synaptic.One you don´t want anymore mark for complete remove.

---

### Post by mahy on 2007-04-11
```
sudo update-alternatives --config java
```

will list all java virtual machines installed (and recognized). The choice is yours.

---

### Post by stchman on 2007-04-11
> **Franscisco said:**
> Does anyone know which Java version is running on my computer(ubuntu)?
how can I get rid of that version?

First off type java -version at a terminal.  Second if you uninstall Java you wont be able to run Java applications and some webpages use Java.

---

### Post by digital_sabotage on 2007-06-29
...thank you mahy  ...you're awesome:-)

---


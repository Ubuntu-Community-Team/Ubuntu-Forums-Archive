---
title: "[SOLVED] How do I change to a different JAVA?"
date: 2007-12-31
forum: General Help
---

### Post by kingrattus on 2007-12-31
> Name@Box:~$ mercury
Mercury does not run on Blackdown Java.
Please, make sure to have the Sun Java version 1.5 or later installed.

How do I remove Blackdown Java & install the latest Sun Java?

Add Remove wont let me do it.

---

### Post by taurus on 2007-12-31
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
Which version of java does the last command print?

---

### Post by PmDematagoda on 2007-12-31
You can change which Java you use by executing:-
```
sudo update-alternatives --config java
```

---

### Post by kingrattus on 2007-12-31
Thank you very much! 
Mercury now works :)

---


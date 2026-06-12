---
title: "Java does NOT work"
date: 2007-10-27
forum: General Help
---

### Post by .Michael on 2007-10-27
Java is the most problematic program/library/enviroment ever created.

It is a pain in the *** to get it to work.

Anyway, how do I set the regular java as my primary java thingy in firefox?

---

### Post by taurus on 2007-10-27
You can either use synaptic and Search for sun-java and install version 6 and the plugin or you can do it from a terminal with

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-font
java -version
```

---

### Post by chipbuddy on 2007-10-30
i wasn't finding sun-java6-**font**, so i tried sun-javaj6-**fonts** and that seemed to work

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```[/QUOTE]

---


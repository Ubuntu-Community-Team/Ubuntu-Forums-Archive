---
title: "Latest java question...."
date: 2007-12-18
forum: General Help
---

### Post by Drags111 on 2007-12-18
Hey, whats the latest sudo apt get for java? I did java -version and it said mine was 1.5.0, so i need to update :S

---

### Post by Drags111 on 2007-12-18
crap this turned into a problem XD

It SAYS i already have java6, but when I do java -version in terminal it says 1.5.0. When I go to eclipse, the highest It says I have is 1.5.0

---

### Post by taurus on 2007-12-18
What's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by FuturePilot on 2007-12-18
You probably have to tell the system to use Java 6 instead of Java 5
```
sudo update-alternatives --config java
```
It should list all the versions of Java installed. Pick the number for Java 6.

---

### Post by Drags111 on 2007-12-18
o well i just uninstalled and reinstalled, and I THINK it works now =]

---


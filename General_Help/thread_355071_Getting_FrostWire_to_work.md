---
title: "Getting FrostWire to work"
date: 2007-02-06
forum: General Help
---

### Post by BWF89 on 2007-02-06
I installed FrostWire. But it wouldn't work and I realized I needed to install Java JRE. So go to install it using Adept. Tried it a few times and every time it froze on 36% when it was preparing to install. So I download and install the self extracting JRE and JDK files from Sun's website.

But just as before whenever I go to use FrostWire I see the icon jumping up and down as is in KDE, but nothing happens.

---

### Post by taurus on 2007-02-06
Let's see if you have the right version of java in your machine.  What's the output of this command from a terminal?

```
java -version
```

---

### Post by BWF89 on 2007-02-06
Says 1.4.2

---

### Post by BWF89 on 2007-02-14
bump

---

### Post by rsambuca on 2007-02-14
I believe you need v1.5

Enable the multiverse repositories

Then simply 
sudo apt-get update
sudo apt-get install sun-java5-jre

---

### Post by BWF89 on 2007-02-15
Thank you

---


---
title: "OpenProj"
date: 2008-07-09
forum: General Help
---

### Post by Briandr on 2008-07-09
How do I install OpenProj on Kubuntu? I downloaded it and ran the executable (.deb) but it seemed to hang. Could not find it anywhere. No good documentation appears to exist. Thanks.

---

### Post by lamego on 2008-07-09
> **Briandr said:**
> How do I install OpenProj on Kubuntu? I downloaded it and ran the executable (.deb) but it seemed to hang. Could not find it anywhere. No good documentation appears to exist. Thanks.

.debs are not run, they are installed.

Open a terminal, cd the directory where it was downloaded and install it with:
```
sudo dpkg -i package.deb
sudo apt-get install -f
```

---

### Post by Briandr on 2008-07-09
Thanks. Still trying to make the transition over. Been long time since I used a command line interface. Have to go back to my dos days.

.....That aside. The documentation does need to improve.

---

### Post by Briandr on 2008-07-09
I got it installed. Now I just need to fix the java issue. Apparently I got Java from the vendor known as 'Free Software Foundation'. OpenProj wants the Sun Java version, which I apparently don't have. It tells me my runtime java is 'Java'. It then proceeds to tell me I can make edits if my java is newer or to force an autodetect. 

Is an autodetect my best option and if so how do I make the change? Which program do I need to use to make the edit?

---

### Post by Vadi on 2008-07-15
You can also just double-click on a .deb to install it. Click [here]("apt:sun-java6-jre") to install sun java

---


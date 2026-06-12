---
title: "Java Runtime Environment"
date: 2008-05-22
forum: General Help
---

### Post by Paris Heng on 2008-05-22
Dear,

How to install the Java Runtime Environment in Ubuntu? Just apt-get install? But what is the name? Any how to?

> apt-get install <name>

---

### Post by yaknowwat on 2008-05-22
You are making things harder than they need to be.

You do not need to do apt-get install for everything anything accessible with apt-get install <name> is in the synaptic package manager there is also Add/Remove for a more clean looking application lister with ratings on things but it does not list everything.

Assuming you are using Ubuntu (GNOME)


You can get to Add/Remove... via

Applications > Add/Remove...


You can get to Synaptic Package Manager via

System > Administration > Synaptic Package Manager


Both of these have a built in search, so search for "Java Runtime Environment" or "JAVA"

---

### Post by prshah on 2008-05-22
> **Paris Heng said:**
> 
How to install the Java Runtime Environment in Ubuntu? Just apt-get install? But what is the name? Any how to?

You can use either java6 (recommended) or java5, and either jre (for normal usage) or jdk (for development of java apps).

Accordingly, select _one_ of the following:
```

sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-jdk
sudo apt-get install sun-java5-jre
sudo apt-get install sun-java5-jdk

```

---

### Post by Paris Heng on 2008-05-22
Thank you to both of you.

---


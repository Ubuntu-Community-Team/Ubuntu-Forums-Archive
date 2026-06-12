---
title: "Java 10.0.1 configuration"
date: 2018-05-12
forum: General Help
---

### Post by jikaz on 2018-05-12
Hello everyone,

I'm a new member. I'm beginning in the programming field. I need help configuring java 10.0.1 on my computer. As you can see in the picture in attachement(synaptic package manager), that java-10.0.1 is installed on my computer. Yet when I write a code and try to compile, it says that I need to install jdk8 (which I presume it's the pervious version of java). Now I thought of maybe I need to install the compiler seperatly from the Java-source-program. But when I try to run a code (without compiling it), it doesnt show an error message, but the same saying that I have to install jdk (picture in attahments).
My question: How do I compile and run programs (from terminal) using jdk-10.0.1 ?[ATTACH=CONFIG]279676[/ATTACH][ATTACH=CONFIG]279677[/ATTACH]

---

### Post by &amp;KyT$0P# on 2018-05-13
Where did you get that [FONT=Courier New]jdk-10.0.1[/FONT] package?  As far as I can tell it's not from the standard repositories.

If you install the Openjdk 10 from the standard repositories, does it work? -
```
sudo apt-get install openjdk-11-jdk
```
(The "11" is not a typo.  The package for Openjdk 10 is really called "openjdk-11-jdk".)

---


---
title: "Where can I specify a version of Java for Eclipse to use?"
date: 2007-05-18
forum: General Help
---

### Post by jmags on 2007-05-18
I made the mistake of installing Eclipse before Sun-Java and now, even though Sun-Java is my primary Java alternative (i.e.: it's what is returned when I type java -version into a term), Eclipse is still running on gcj. How can I fix this?

---

### Post by thelinuxguy on 2007-05-19
Edit or create the file
~/.eclipse/eclipserc

and add
JAVA_HOME=<path to your jdk>

You may need to clean your project.
Project >> clean

---

### Post by jmags on 2007-05-19
Thanks. While I was poking around I also discovered there is a java_home file in /etc/eclipse that can be used to modify this setting for all users.

---


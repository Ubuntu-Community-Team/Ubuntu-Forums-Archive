---
title: "Java and OpenOffice"
date: 2007-12-12
forum: General Help
---

### Post by deamon_knight on 2007-12-12
Looks Like a number of people have been having this problem  but I haven't been able to find a solution.

I'm Running OopenOffice 2.3 in Xubuntu Gutsy, and it won't properly detect Java. Java is installed.
Java -version reports: 1.6.0_03

Java --config says there is only one installed java version, nothing to config.

Attempts to point OpenOffice to the directory
/usr/lib/jvm/java-6-sun/jre/bin/java fail, says this directory does not contain a java runtime enviornment.

Any advice?

---

### Post by luisromangz on 2007-12-12
/usr/lib/jvm/java-6-sun/jre/bin/java is not a directory, you should try using just /usr/lib/jvm/java-6-sun

---

### Post by deamon_knight on 2007-12-12
Tried that, and the Jre subdir. I'm stumped

---

### Post by deamon_knight on 2007-12-13
The Solution appead to be an "Apt-get install openoffice.org" rather than using synaptic to install the different apps piecemeal. I don't know what this worked instead, but it did.

---

### Post by wonko123 on 2008-05-23
Ran into the same problem today - seems like installing package "**openoffice.org-java-common**" made the difference on Kubuntu Hardy.

---


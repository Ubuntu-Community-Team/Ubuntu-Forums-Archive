---
title: "Synaptic fail to install java, forbidden package...?"
date: 2008-05-19
forum: General Help
---

### Post by pompiuses on 2008-05-19
I'm trying to install package "sun-java5-jdk" from synaptic package manager. I keep getting the following error:

W: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb](http://no.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb)
  403 Forbidden

W: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb](http://no.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb)
  403 Forbidden

etc etc....

What's wrong??

---

### Post by joshsmith on 2008-05-19
looks like a dead mirror, go into system>admin>software sources, and change the download location

---


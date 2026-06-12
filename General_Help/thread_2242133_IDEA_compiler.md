---
title: "IDEA compiler"
date: 2014-08-30
forum: General Help
---

### Post by freewarelover on 2014-08-30
Hello I didn't see a general software subforum so I hope here is ok. I googled to see if the IDEA compiler/IDE for Java is available for ubuntu although it seems to be I can't seem to install it. I'll list the two links I found and the issues I had with them. 

**link **[http://wiki.jetbrains.net/intellij/Installing_and_running_IntelliJ_IDEA_on_Ubuntu](http://wiki.jetbrains.net/intellij/Installing_and_running_IntelliJ_IDEA_on_Ubuntu)
**Issue **In the step where you put try to instal the jre and jdk it doesn't work. I replaced replaced the 6 with 7 because that's what I need.

**link **[https://apps.ubuntu.com/cat/applications/intellij-idea-ce/](https://apps.ubuntu.com/cat/applications/intellij-idea-ce/)

**issue **the button that's suppose to take me to the software center takes me to where the software sources are enabled saying that none of the sources provide it.

---

### Post by QIII on 2014-08-30
Hello!

Take care when following old instructions.  They are often not worth a plug nickel.

The Lucid repositories have been moved since Lucid is EOL (unless you have the server version).  Besides that, Oracle decreed that nobody could keep their stuff in repositories, so you wouldn't find it anyway.

The very best way to install is to look [here]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") for Oracle Java 7 or [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") for Oracle Java 8.  The PPAs contain scripts to automate downloading Oracle Java 7 or 8 from Oracle's website, install it as Ubuntu expects it to be installed and then set it as the preference.  Webupd8.org is like everyone else:  They can't keep the Oracle binaries in a repo.  What you get is a nice installer.

As for the rest of what you are doing, I can't be of much help.

Cheers!

---

### Post by freewarelover on 2014-08-30
Actually getting the jdk may not be necessary for me since I already did it for drjava but wasn't sure if I had to it again in a different way for the different IDE. My class will be moving from drjava to IDEA so that's why I was trying to install both.

---

### Post by freewarelover on 2014-09-07
Bump. I assume it has yet to be ported to Linux. I even checked the wine site but it's not in the list. It's not that I don't like eclipse (although it can possibly be a bit of a pain to debug with) it's just that ( I think) I'm soon going to be required by my school to use intellJ IDEA and I'd prefer to stay in linux boot as much as possible.

---


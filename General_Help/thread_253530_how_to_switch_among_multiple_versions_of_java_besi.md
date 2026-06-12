---
title: "how to switch among multiple versions of java besides using update-alternative?"
date: 2006-09-08
forum: General Help
---

### Post by Alex.X.Zhang on 2006-09-08
does anybody know how to switch among multiple versions of java without using update-alternative?
By switching I mean set the entire java environment, such as java_home, java, javac, and add java/bin into path. 

I came from the gentoo world. In gentoo there is a util called java-config, which allows one to set system vm or user vm. what it does is creating a file like this:

JDK_HOME=/opt/jdk1.5.0_06-amd64
JAVAC=/opt/jdk1.5.0_06-amd64/bin/javac
PATH=/opt/jdk1.5.0_06-amd64/bin:/opt/jdk1.5.0_06-amd64/jre/bin:${PATH}
# VERSION="jdk1.5.0_06-amd64"
MANPATH=${MANPATH}:/opt/jdk1.5.0_06-amd64/man
JAVA_HOME=/opt/jdk1.5.0_06-amd64

Then you can source this file in your .bashrc or .bash_profile.

Is there anything similar in ubuntu? If not, is anybody interested in writing one? I am interested if someone can be a mentor. I have never done any linux programming before. 

thank you.

---

### Post by brecke on 2007-09-10
hi there!

I kinda have the same problem and i kinda come from the gentoo world as well.. where it only takes the "eselect" command to change between different java versions. I need to be able to do the same in ubuntu but i just dont know how.

Any help would be greatly appreciated.
Thanks in advance,

EDIT: Oh wait!! i think i found it! "sudo update-alternatives --config java" seems to do it... nice! :)

---


---
title: "Installing jdk1.5 and IntelliJ IDEA 5.0"
date: 2005-09-02
forum: General Help
---

### Post by breeze on 2005-09-02
Hi,
I have installed jdk1.5 and set the path in /home/breeze/.bashrc as 

PATH=$PATH:/path/to/java/home/bin

**Martin, Thanks for helping me on this**.

Im going to install **IntelliJ IDEA 5.0** and now its giving me an error as:

ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
Exception in thread "main" java.lang.NoClassDefFoundError: com/intellij/idea/Main

in idea.sh file I have set the IDEA_JDK as :
IDEA_JDK=$JAVA_HOME

Please help me on this.

Thanks in advance,

breeze

---

### Post by Pikapooh on 2005-09-02
Set JDK_HOME variable, for example:

export JDK_HOME=/usr/lib/j2sdk1.5-sun/

Then run idea.sh

---


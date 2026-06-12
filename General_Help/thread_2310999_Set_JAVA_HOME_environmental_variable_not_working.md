---
title: "Set JAVA_HOME environmental variable not working"
date: 2016-01-23
forum: General Help
---

### Post by declan.marks on 2016-01-23
I'm trying to set the JAVA_HOME environmental variable. This is for Intellij, Pycharm, PHPStorm and many programs that require java. I have removed OpenJDK and install oracles version.

I have added "export JAVA_HOME=/Apps/JDK" to /etc/environment. When I log off and log back in and go into the terminal and enter echo $JAVA_HOME I get a blank line. I type sources /etc/environment, then the previous line shows the contents of the variable.

I have also tried adding it to /etc/profiles, which didn't work. I want JAVA_HOME to be accessible for every user on the system. 

Why doesn't the variable load at login?

---

### Post by dragonfly41 on 2016-01-23
I have added the following lines ..
```

export JAVA_HOME="/usr/lib/jvm/java-8-oracle"
export PATH="${PATH}:$JAVA_HOME/bin"


export JAVA_JRE="/usr/lib/jvm/java-8-oracle/jre"
export PATH="${PATH}:$JAVA_JRE/bin"

```

in ~/.profile

But that is for one user.

---


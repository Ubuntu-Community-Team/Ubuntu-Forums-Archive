---
title: "/etc/profile"
date: 2005-08-05
forum: General Help
---

### Post by go_bears on 2005-08-05
I modified the /etc/profile to create a system-wide $JAVA_HOME environment variable and to add $JAVA_HOME/bin to the $PATH.  I basically appended the following to my /etc/profile.

```
JAVA_HOME=/usr/java/j2sdk1.4.2_08
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
export PATH
```

The changes don't work even after rebooting the computer.  Any suggestions?  I thought /etc/profile was read during startup...  :confused:

---

### Post by Rule on 2005-08-05
sudo gedit /etc/bash.bashrc

 JAVA_HOME=/usr/java/<java version>
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

---

### Post by go_bears on 2005-08-05
Thanks for the tip.  

I was following instructions in the book *Professional Apache Tomcat 5* on how to install the SDK.  They mentioned using /etc/profile for system wide settings, but they failed to mention /etc/bash.bashrc.

---

### Post by go_bears on 2005-08-05
found this after i googled "/etc/bash.bashrc"... in case anyone else is wondering the difference between /etc/profile and /etc/bash.bashrc.

[http://archives.free.net.ph/message/20050720.061648.13545337.en.html](http://archives.free.net.ph/message/20050720.061648.13545337.en.html)

---


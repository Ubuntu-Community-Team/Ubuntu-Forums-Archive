---
title: "set JAVA_HOME in kubuntu"
date: 2007-07-25
forum: General Help
---

### Post by netvampire on 2007-07-25
Hey,
I am puzzled by this. I have Kubuntu feisty, with java6 installed. I also have apache tomcat installed. Tomcat, upon startup, says that JAVA_HOME is not intialized. OKAY, no big deal. I did a quick search on this forum to find that i set that variable in /etc/environment. Done, tested, and failed. Someone else suggested editing .bashrc and adding 'export java_home=path to java dir' ... Done, and failed.

I am not sure if that advice only worked for ubuntu and not kubuntu.

Can anyone please tell me how to set up the JAVA_HOME environment variable in kubuntu. thanks

---

### Post by bettlebrox on 2007-07-25
Is this a typo?

export java_home=path to java dir' ..

It should:

export JAVA_HOME=path to java dir' ..

---

### Post by netvampire on 2007-07-25
yeah i was too lazy to hit the shift key. 

I did indeed type JAVA_HOME in both /etc/environment and ~/.bashrc however in both I have had no luck.

Can anyone please help me with this.

Thanks :)

---

### Post by netvampire on 2007-07-25
Fixed. Needed to reboot.

---

### Post by bettlebrox on 2007-07-26
Logging out and back in again will do it too.

---


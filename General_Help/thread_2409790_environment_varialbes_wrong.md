---
title: "environment varialbes wrong"
date: 2019-01-06
forum: General Help
---

### Post by pelgrim on 2019-01-06
I needed to change my java version back to jdk 6

for some reason I can't get my environtment variables to change, so for example 
JAVA_HOME=/usr/lib/jvm/java-11-oracle

tried:
export JAVA_HOME=...
putting a line in /etc/environment
env JAVA_HOME=...

nothing works, it sticks to the old value "/usr/lib/jvm/java-11-oracle"

I purged java 11 from my system by the way.

---

### Post by TheFu on 2019-01-07
**unset JAVA_HOME**
[https://www.tecmint.com/set-unset-environment-variables-in-linux/](https://www.tecmint.com/set-unset-environment-variables-in-linux/) has more details.  Of course, controlling environment vars is dependent on the shell you run.  tcsh works differently than ksh or bash or zsh or psh or fish .... 

Not really a good idea to touch /etc/environment. Better to only modify the environment for the specific userids that need it. After all, you might need/want to have 4 different versions of Java installed and used by different projects concurrently.

---


---
title: "How to get Ubuntu to use newer version of a program?"
date: 2014-10-29
forum: General Help
---

### Post by Bobby_James on 2014-10-29
I have a program which says: "CMake 2.8.11 or higher is required.  You are running version 2.8.7."

In /usr/share/ I have two cmake directories: cmake-2.8 and cmake-3.0.2.

What I would like to do is have Ubuntu always use cmake 3.0.2 rather than 2.8.

How do I set this? More broadly, how can I in future say to Ubuntu: use this newer version and forget about the older version?

Thanks!

---

### Post by ian-weisser on 2014-10-29
Uninstall the 2.8 package and it's dependencies.
Then reinstall the 3.0 version.
You want /usr/bin/cmake installed by the 3.0 version.

---

### Post by Alireza_Zamani on 2014-10-29
hi
i think you need add some lines to /etc/profile file , read this pages carefully : 

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[http://askubuntu.com/questions/730/how-do-i-set-environment-variables](http://askubuntu.com/questions/730/how-do-i-set-environment-variables)

for example for Java SE i add this lines :

JAVA_HOME=/usr/local/java/jre1.7.0_21
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH

and now Ubuntu use JRE Instead of OpenJDK .
but OpenJDK still installed .

good luck

---


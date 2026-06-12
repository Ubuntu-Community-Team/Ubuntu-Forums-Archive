---
title: "SQL developer installing"
date: 2007-12-18
forum: General Help
---

### Post by dominik_ap on 2007-12-18
Hi, i am quite beginner in ubuntu, i love it, but i have also a lot of troubles :)

i am trying to run SQL developer application, but when i write 
 sh /opt/sqldeveloper/sqldeveloper.sh

it prints the output
Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.

/opt/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 478: 14065 Aborted                 (core dumped) ${JAVA} ${APP_VM_OPTS} ${APP_SCRIPT_USER_HOME} ${APP_ENV_VARS} -classpath ${APP_CLASSPATH} ${APP_MAIN_CLASS} ${APP_APP_OPTS}


I know i need to have installed Java 5 or higher, i tried to install it by adept manager and i installed SUN JAVA 6 bin package...

should i do smth more? Or where is the problem?

Thank you very much


Dominik Franek

---

### Post by mennan on 2008-02-08
Install JDK.

mennan@mennan-laptop:~/Desktop/sqldeveloper$ ./sqldeveloper.sh

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

/home/mennan/Desktop/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 478: 10281 Aborted                 (core dumped) ${JAVA} ${APP_VM_OPTS} ${APP_SCRIPT_USER_HOME} ${APP_ENV_VARS} -classpath ${APP_CLASSPATH} ${APP_MAIN_CLASS} ${APP_APP_OPTS}
mennan@mennan-laptop:~/Desktop/sqldeveloper$ 


mennan@mennan-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
mennan@mennan-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

mennan@mennan-laptop:~$ export JAVA_HOME=/home/mennan/Desktop/jdk1.5.0_14
mennan@mennan-laptop:~$ export PATH=$JAVA_HOME/bin:$PATH
mennan@mennan-laptop:~$ echo $JAVA_HOME
/home/mennan/Desktop/jdk1.5.0_14
mennan@mennan-laptop:~$ ./.profile
mennan@mennan-laptop:~$ echo $JAVA_HOME
/home/mennan/Desktop/jdk1.5.0_14

mennan@mennan-laptop:~/Desktop/sqldeveloper$ ./sqldeveloper.sh
Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

Using oracle.home=/home/mennan/Desktop/sqldeveloper
Using ide.user.dir=/home/mennan/.sqldeveloper
Addin: Translator PlSql is trying to register a input type (.plsql) which conflicts with translator PlSql who already using this input type
...
...

---

### Post by mlayog on 2008-03-06
Mennan:

Would you happen to have a step by step guide on how to install Oracle SQLDeveloper on Ubuntu? I'm a bit of a newbie when it comes to installing SQLDeveloper on Linux.

Thanks for your time.

---

### Post by jtsop on 2008-05-12
with out being able to verify all steps (all my computers have all of those allready installed) so if something does not work tell me to help you out.

download sqldeveloper-rpm ([http://download.oracle.com/otn/java/sqldeveloper/sqldeveloper-1.5.53.38-1.noarch.rpm](http://download.oracle.com/otn/java/sqldeveloper/sqldeveloper-1.5.53.38-1.noarch.rpm))

then:

sudo apt-get install lsb sun-java6-jre alien 
sudo alien --scripts sqldeveloper*rpm
sudo dpkg -i sqldeveloper*deb

---


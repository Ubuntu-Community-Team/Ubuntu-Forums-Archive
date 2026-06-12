---
title: "JavaHMO + Ubuntu 5.04"
date: 2005-09-24
forum: General Help
---

### Post by metrounit9 on 2005-09-24
Trying to get JavaHMO for TiVo running on Ubuntu 5.04.

I used alien to convert JavaHMO from .rpm to .deb

Also pretty sure that Java 1.4.2 and Advanced Imaging are installed correctly.

If I do java -version, I get the correct version information.

I found the JavaHMO 'init' in /etc/rc.d/init.d/ and edited the variable for Java JRE and copied to /etc/init.d/, but still get a message that Java JRE couldn't be located.

Java JRE is install in /usr/lib/javajre

JavaHMO.init includes the following:
JAVA_HOME=/usr/lib/javajre
if [ "$JAVA_HOME" == "" ] ; then
for java in `ls /usr/local/java 2>/dev/null` ; do
if [ "${java%j2re*}" == "" ] ; then
export JAVA_HOME=/usr/local/java/$java
break
elif [ "${java%j2sdk*}" == "" ] ; then
export JAVA_HOME=/usr/local/java/$java/jre
break
fi
done
fi

if [ "$JAVA_HOME" == "" ] ; then
echo "Error: Could not locate JRE. Please make sure you have the Sun JRE or JDK installed. If it is installed, then try setting your JAVA_HOME environment var.";
exit

I am sure I'm missing something...but I don't know what!

---

### Post by phex on 2005-09-24
so what is not running? if you type in "java -version" and you get the correct information, it should run fine?

Nevertheless, I looked at the script you have to export the JAVA_HOME variable: export JAVA_HOME
because in your script the conde inside the if command
if [ "$JAVA_HOME" == "" ] ; then
....
fi
is never invoked/called. ;) 
try to type in "echo $JAVA_HOME", it should print nothing if you use this script. 

Have you installed Java SDK or only Java JRE? because the path /usr/local/java signals that you have installed the SDK somewhere. ;) I would also suggest to type echo $PATH. I am quite sure you have another Java Virtual Machine somewhere installed on your PC and this is used instead of your /usr/lib/javajre installation.

---

### Post by metrounit9 on 2005-09-28
Just in case anybody else has this problem:

I Finally was able to get the Java HMO configuration gui running. I needed to set the JAVA_HOME= variable inside the JavaHMO script located in the /usr/bin directory.

In my case, I needed to add "JAVA_HOME=/usr/lib/j2re1.4-sun" to the above mentioned JavaHMO script.

---


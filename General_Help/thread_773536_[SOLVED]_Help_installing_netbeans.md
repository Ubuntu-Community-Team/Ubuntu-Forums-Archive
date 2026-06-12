---
title: "[SOLVED] Help installing netbeans"
date: 2008-04-28
forum: General Help
---

### Post by Diabolis on 2008-04-28
I downloaded the installer from the netbeans page and tried to execute it and this error shows up:
```
**./netbeans-6.1-javase-linux.sh** 
Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit http://java.sun.com/javase/downloads

```

I have set a JAVAHOME environment variable and I know its working because I use Jajuk which uses the Java run time environment. Also see this:
```
**echo $JAVAHOME**
/home/gaston/programming/JAVA/bin/jdk1.6.0_03/bin

**java -version**
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

So I tried to install it by using the **--javahome** argument and still no luck.
```
**./netbeans-6.1-javase-linux.sh --javahome $JAVAHOME**
Configuring the installer...
Searching for JVM on the system...
Java Runtime Environment (JRE) was not found at the specified location /home/gaston/programming/JAVA/bin/jdk1.6.0_03/bin

```

---

### Post by Diabolis on 2008-04-28
This very strange, I hope someone has an idea of what is going on.

I installed java from the repositories with this command:
```
sudo apt-get install sun-java6-jdk
```

I have set my PATH environment variable in my .bashrc file like this:
```
PATH=$JAVAHOME:$PATH
```
So my old java installation is still used.
```
**java -version**
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```


Here is when it gets weird. I ran the netbeans installer and it worked, but it didn't used the old java installation. It used the new one even when I have modified my PATH variable. It picked this JDK:
```
/usr/lib/jvm/java-6-sun
```

I changed the route to the old java installation (*/home/gaston/programming/JAVA/bin/jdk1.6.0_03/bin*) and it says that the folder does not contain a JDK!

---

### Post by amohanty on 2008-04-29
You might want to try it without the trailing **/bin**

hth
AM

---

### Post by Diabolis on 2008-04-29
This is driving me nuts. Removing the last bin folder from the path while using the --javahome argument worked.

If I remove the bin folder from my environment variable (*JAVAHOME*), then my java installation doesn't work. Meaning that the installation from the repositories is used.
```

*JAVAHOME=/home/gaston/programming/JAVA/bin/jdk1.6.0_03*
**java -version**
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

*JAVAHOME=/home/gaston/programming/JAVA/bin/jdk1.6.0_03/bin*
**java -version**
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

At least it worked.
Is just annoying to play around with the paths just to get installed an application when environment variables should take care of this.

Thank you for the tip.





Now I get it, I hope this saves someone's time.

**NOTE:**
Netbeans adds by itself the *bin* folder to the end of whatever path you give to it while choosing a JDK folder. So an environment variable will not work, you have to specify the path by hand.

---

### Post by amohanty on 2008-04-29
actually JAVA_HOME should always point to the folder _containing_ the bin, lib, folders. If you dont to development and hava a jdk it should point to the JDK_HOME/jre folder (which you will notice also has the bin,lib folders)

to select which jvm you want to use:
sudo update-alternatives --config java

hth
am

---


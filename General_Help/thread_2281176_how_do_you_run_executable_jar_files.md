---
title: "how do you run executable jar files?"
date: 2015-06-05
forum: General Help
---

### Post by matthewland123 on 2015-06-05
i have tried to install it via the software center and that failed, i have also downloaded this file [http://www.oracle.com/technetwork/ja...s-2133155.html]("http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html") but it just gives me more jar files i cant install, please help.

---

### Post by dino99 on 2015-06-05
[http://stackoverflow.com/questions/24430394/how-to-run-jar-file-on-start-up-in-ubuntu](http://stackoverflow.com/questions/24430394/how-to-run-jar-file-on-start-up-in-ubuntu)
[http://askubuntu.com/questions/521119/running-jar-file-using-jdk-on-ubuntu-14-04](http://askubuntu.com/questions/521119/running-jar-file-using-jdk-on-ubuntu-14-04)

---

### Post by kulen19 on 2015-06-05
Welcome to Ubuntuforums!

You can run it with ```
java -jar yourfile.jar
``` But if you have several files ending in jar, are you sure this is what you want to do?

It looks like you are trying to install java. I think openjdk still is the best choice(though I'm not sure). I suggest first check if you already installed it, since it seems you tried to, and you may have succeeded. You insert these command at the command-line interface (Alt+f2 -> gnome-terminal)

```
 java -version 
```

```
sudo apt-get update
``` 

then 

```
sudo apt-get install default-jre
``` to install the current run-time environment. 

If you need the developer kit(JDK), e.g. if you need to compile Java programs run:

```
sudo apt-get install default-jdk
```

---

### Post by flaymond on 2015-06-05
Run it with ***java -jar file.java***, and make sure it ***runable.***&#8203;


If you want a set of Java development tools, run


```
sudo apt-get install openjdk-7-jdk
```

It will install Java Development Kit (7) with a few extras libraries. ;)


If you want to look for more additional programs, libraries or softwares.

run ```
apt-cache search <your_program_name>
```

to see if the program available in ubuntu repositories.

---


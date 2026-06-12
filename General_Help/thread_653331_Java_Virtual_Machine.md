---
title: "Java Virtual Machine"
date: 2007-12-29
forum: General Help
---

### Post by drsaamah on 2007-12-29
I've installed Matlab Student Version 7 on my computer running Gutsy Gibbon.  When I go to the command line and try to run it I get the following error:
```
saam@euler:~$ awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.

```

I thought I had Java but maybe not, so I proceeded to go to the terminal and "sudo apt-get install" EVERYTHING with the word java in it, and I still get the same error.  A friend of mine installed the same version of Matlab on this same computer when I was using Fiesty and it worked fine.  Any thoughts? I appreciate any help in advance.

---

### Post by taurus on 2007-12-29
What's the output of this command?

```
java -version
```
If you want to install java, try

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by drsaamah on 2007-12-29
The output is:
```
saam@euler:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

As for your suggestion, all that was already installed, as you can see:
```
saam@euler:~$ sudo apt-get update
[sudo] password for saam:
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:5 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://archive.canonical.com gutsy Release                       
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release                     
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources                  
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Sources     
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Hit http://us.archive.ubuntu.com gutsy/universe Sources              
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages           
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources            
Hit http://security.ubuntu.com gutsy-security/universe Packages      
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages         
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 953B in 4s (193B/s)
Reading package lists... Done
saam@euler:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
saam@euler:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
saam@euler:~$ matlab
saam@euler:~$ awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.


```
Any other thoughts?

---

### Post by taurus on 2007-12-29
See if it works with Java 1.6 because you have version 1.4 as default right now.

```
sudo update-alternatives --config java
```
Make sure you pick version 1.6 as your default from the output.

To be sure after you have selected it, run this command again from a terminal.

```
java -version
```

---

### Post by drsaamah on 2007-12-29
eh, I'm so sorry.  I should be better with Linux by now...
I don't know which of these options is version 1.6:
```
saam@euler:~$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-7-icedtea/jre/bin/java
*+        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/bin/jamvm
          6    /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: 

```

---

### Post by taurus on 2007-12-29
> **drsaamah said:**
> eh, I'm so sorry.  I should be better with Linux by now...
I don't know which of these options is version 1.6:
```
saam@euler:~$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          **[COLOR="Blue"]2    /usr/lib/jvm/java-6-sun/jre/bin/java[/COLOR]**
          3    /usr/lib/jvm/java-7-icedtea/jre/bin/java
*+        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/bin/jamvm
          6    /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: 

```

#2.

---

### Post by drsaamah on 2007-12-29
actually I just tried all 6 options and im still getting the same error on executing matlab. :-(

---

### Post by drsaamah on 2007-12-29
Here was the output:
```
saam@euler:~$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-7-icedtea/jre/bin/java
 +        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/bin/jamvm
*         6    /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
saam@euler:~$ matlab
saam@euler:~$ awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.

saam@euler:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
saam@euler:~$ matlab
saam@euler:~$ awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.


```

---


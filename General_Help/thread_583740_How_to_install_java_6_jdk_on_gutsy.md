---
title: "How to install java 6 jdk on gutsy?"
date: 2007-10-20
forum: General Help
---

### Post by ehdtkqorl123 on 2007-10-20
I tried to install

sudo aptitude install sun-java6 but it says 

[sudo] password for sungq:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "sun-java6".  However, the following
packages contain "sun-java6" in their name:
  sun-java6-plugin sun-java6-demo sun-java6-fonts sun-java6-bin 
  sun-java6-doc sun-java6-jdk sun-java6-jre sun-java6-source 
  sun-java6-javadb 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  



IT seems like I have java1.4 on Gutsy, but somehow java6 is not installed..
How can i install it?

---

### Post by FuturePilot on 2007-10-20
> **ehdtkqorl123 said:**
> I tried to install

sudo aptitude install sun-java6 but it says 

[sudo] password for sungq:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "sun-java6".  [B]However, the following
packages contain "sun-java6" in their name:[/B]
  sun-java6-plugin sun-java6-demo sun-java6-fonts sun-java6-bin 
  sun-java6-doc **sun-java6-jdk** sun-java6-jre sun-java6-source 
  sun-java6-javadb 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  



IT seems like I have java1.4 on Gutsy, but somehow java6 is not installed..
How can i install it?

```
sudo apt-get install sun-java6-jdk
```
jdk is a Java Development Kit. You don't need this unless you are developing a Java app or something. If you're looking for the Java Runtime Environment and Firefox Plugin you need to do this
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by ehdtkqorl123 on 2007-10-20
I am installing it for development purpose, but weirdly I get this msg

sungq@sungq-desktop:~$ sudo apt-get install sun-java6-jdk
[sudo] password for sungq:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Where exactly is Java installed?
In /etc/j2se, I have a directory called 1.4 but nothing else.

---

### Post by FuturePilot on 2007-10-20
It  should be in /usr/lib/jvm

---

### Post by ehdtkqorl123 on 2007-10-20
yEA in there I have java-6-sun-1.6.0.03 and files for java sdk.
However when I try to check version,

$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
sungq@sungq-desktop:/var/cache/apt/archives$ 


It says version is too low to run Eclipse.
Why doesn't Eclipse recognize newly installed Java sdk??

---

### Post by FuturePilot on 2007-10-20
Perhaps try
```
sudo update-alternatives --config java
```

---

### Post by ehdtkqorl123 on 2007-10-20
Awesome, that worked ! Thank you!

---

### Post by FuturePilot on 2007-10-20
No problem. Glad it's working ;)

---

### Post by Gregory_NZL on 2007-10-20
I tried installing the Java JDK on Ubuntu 7.10 with apt-get unfortunately it failed for me. 

I did some more searching around and found these manual instructions which are valid for both Ubuntu and Debian. 
[http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation_manually](http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation_manually)


**These are the commands I used to install the Java JDK binary**

You have to dowload the latest Java JDK (in this case, jdk-6u3-linux-i586.bin) from the Sun Java site.

Change directory to /usr/local/lib

```
cd /usr/local/lib
```

From there extract the JRE or JDK archive file you downloaded:

```
sudo sh /some/path/jdk-6u3-linux-i586.bin
```

In the above commands, replace /some/path with where the JRE/JDK .bin/.tgz resides and of course replace the filename with what it actually is in your case.

Now create some symlinks so that the executables can be run easily. Change directory to /usr/local/bin

```
cd /usr/local/bin
```

From there execute the following set of commands:

```
sudo ln -sf ../lib/jdk1.6.0_03/bin/* .
```
        
Pay attention to the period at the end of the command, it is required. And adjust the directory as well to what you have (e.g. jdk1.6.0_03 for the Sun Java 1.6.0_03 JDK).

3 Verify installation

To verify that the installation was successful, execute

```
java -version
```

The output should look something like this if everything is well

```
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

---

### Post by MR.UNOWEN on 2007-10-29
Didn't work with me....

Here's what I got...

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

Here's what I tried to install,,,

jdk-6u3-linux-i586-rpm.bin
and
jre-6u3-linux-i586.bin

I got it to run and it gave me the user agreement and it extracted everything so I don't know what I did wrong.

---

### Post by MR.UNOWEN on 2007-10-30
Can someone help me out?

---

### Post by abadtooth on 2007-11-05
> **FuturePilot said:**
> Perhaps try
```
sudo update-alternatives --config java
```

Thank you!
This helped me get java working finally!
never tried limewire though :P

---


---
title: "Where O Where has my Java Gone?"
date: 2007-07-14
forum: General Help
---

### Post by Goliath! on 2007-07-14
Can any Java gods/goddesses help me out?  My Java used to work, but I broke it and I don't know how to fix it.

I use a great program called Freemind for mind mapping.  I very much recommend it, even though it requires Java jre.

Freemind was working perfectly.  But I noticed one feature wasn't working.  I tried to debug it myself (*dumb*) and determined it was a Java problem.  So I tried to uninstall my jre and install the lastest jre.  That didn't work and I went hog-wild uninstalling and re-installing various versions of Java (1.4, 5, 6) in various ways (Synaptic, Add/Remove Programs, Sun's self-extracting bin file, Automatix, sudo apt-get).  Now my machine is very confused.

Synaptic and Add/Remove Programs tell me I have both Java 5 and Java 6 installed.

If I got to java.com > Do I have Java?, it tells me:
[INDENT]Verified Java Version
Congratulations!
 You have the recommended Java installed (Version 6 Update 2).  
 [/INDENT]
(I use 32-bit Flock.)

But, if I try to check my Java version from the command line I get:
```
john@xan2:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

```

When I try to run Freemind I get:
```
john@xan2:~$ freemind
ERROR:   Couldn't find a java virtual machine,
         define JAVACMD, JAVA_BINDIR, JAVA_HOME or PATH.
         See the manpage of freemind(1) for details.

```

I want Java5 to work (I finally consulted the Freemind forum and found out that Java6 is the cause of my original problem).

I am running 7.04 on Dell 1501 laptop with AMD64.  Note: I also tried the ia32 jre, before I realized ia=Intel Architecture.

update-alternatives doesn't work either:

```
john@xan2:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
john@xan2:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

```

:confused:

---

### Post by taurus on 2007-07-14
What's the output of this command from a terminal?

```
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java -version
```
Or
```
ls -la /usr/lib/jvm/java-1.5.0-sun/jre/bin
```

---

### Post by Goliath! on 2007-07-14
Good questions.  I get:

```
john@xan2:~$ ls -la /usr/lib/jvm/java-1.5.0-sun/jre/bin
total 1184
drwxr-xr-x 2 root root   4096 2007-07-14 12:05 .
drwxr-xr-x 5 root root   4096 2007-07-14 12:05 ..
-rwxr-xr-x 1 root root  66200 2006-12-15 02:59 java
-rwxr-xr-x 1 root root  65136 2006-12-15 03:05 keytool
-rwxr-xr-x 1 root root  65168 2006-12-15 03:06 kinit
-rwxr-xr-x 1 root root  65168 2006-12-15 03:06 klist
-rwxr-xr-x 1 root root  65168 2006-12-15 03:06 ktab
-rwxr-xr-x 1 root root  65392 2006-12-15 03:16 orbd
-rwxr-xr-x 1 root root  65232 2006-12-15 03:16 pack200
-rwxr-xr-x 1 root root  65472 2006-12-15 03:06 policytool
-rwxr-xr-x 1 root root  65136 2006-12-15 03:14 rmid
-rwxr-xr-x 1 root root  65136 2006-12-15 03:14 rmiregistry
-rwxr-xr-x 1 root root  65136 2006-12-15 03:16 servertool
-rwxr-xr-x 1 root root  65392 2006-12-15 03:16 tnameserv
-rwxr-xr-x 1 root root 358821 2006-12-15 03:16 unpack200


john@xan2:~$ /usr/lib/jvm/java-1.5.0-sun/jre/bin/java -version
Error: no `client' JVM at `/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64/client/libjvm.so'.
```

What do you think, doc?  Will she live?

---

### Post by taurus on 2007-07-14
Why don't you open synaptic from System -> Administration -> Synaptic Package Manager and remove both java versions 1.5 & 1.6.  Then, reinstall 1.5 again.

```
sudo aptitude update
sudo aptitude install sun-java5-jre 
java -version
```
p.s.  Remember to close down synaptic before you run those commands from a terminal or you will get an error message saying that you can't run two adepts at the same time.  Otherwise, you can instal Sun's java 1.5 from synaptic if you wish.

---

### Post by Goliath! on 2007-07-14
I really appreciate your help!!

I've been down this road before, but hey, it's a pleasant drive.

I uninstalled java5 and java6 using Synaptics.  Then rechecked it; they are gone.  Then I did the update and the install of sun java5 jre, exactly as you typed.  Everything seemed to go very well.  It spewed a lot of stuff to the terminal, so I couldn't catch it all.  But here's the end result:
```
john@xan2:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
```
Also tried update-alternatives --config java and selected java5.  Then java -version still gave the same output as above (command not found).
:confused:

---

### Post by Goliath! on 2007-07-18
I got this problem fixed after jumping through 4 hoops of fire.  Check out: [http://ubuntuforums.org/showthread.php?t=501918]("http://ubuntuforums.org/showthread.php?t=501918")

---


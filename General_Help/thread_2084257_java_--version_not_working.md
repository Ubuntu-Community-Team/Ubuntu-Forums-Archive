---
title: "java --version not working"
date: 2012-11-14
forum: General Help
---

### Post by BurnDownTheSky on 2012-11-14
All right, I admit to being quite stumped.

I downloaded a little java app, and was having some trouble with it, so I thought i'd switch from OpenJDK to Sun java, using 
```

update-alternatives --config java

```It showed me the various installs of java, and I selected sun 6.  And for some reason, everything then fell apart.  Not only did it not solve my app problem (which I really couldn't care less about now)  java itself went all wonky.

Firstly, ```
java --version
``` doesn't work.  It gives me:

```
Unrecognized option: --version
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

```Also, if I run a shell file containing the line java -jar someprogram.jar that  to run a java app, it does not work.  And yet if I type into the terminal 

```
java -jar ~/somefolder/someprogram.jar
```it DOES work.  So it would appear that java is installed, and the command java seems to be somewhat working.

```
update-alternatives --display java

```gives me:

```
java - manual mode
  link currently points to /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
/opt/java/32/jre1.6.0_30/bin/java - priority 2000
  slave java.1.gz: /opt/java/32/jre1.6.0_30/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/java - priority 1061
  slave java.1.gz: /usr/lib/jvm/java-6-openjdk-i386/jre/man/man1/java.1.gz
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java - priority 1051
  slave java.1.gz: /usr/lib/jvm/java-7-openjdk-i386/jre/man/man1/java.1.gz
Current 'best' version is '/opt/java/32/jre1.6.0_30/bin/java'.

```Also - and even more frustrating...I was trying to run my son's game of minecraft (which is written in java) just to see if another java app would ran.  It worked perfectly.  Then - and don't ask - I accidentally deleted that icon from "Docky".  When I restored it from the trash can, it appeared on the Desktop, and I dragged it back to Docky.

And NOW I am getting a corrupt jar file message when I try and run minecraft, either from the resurrected Docky icon, or from the terminal.   But NOTHING was changed, aside from restoring it from trash!?

I really have no idea what the hell happened, but it all seemed to start when I ran update-alternatives --config java.

Any ideas?  Many thanks in advance.

(Oh yeah...something else...when I type 
```

update-java-alternatives -l

```

it doesn't even list anything from Sun, just the openJDK 6 and 7.

---

### Post by jim_deadlock on 2012-11-15
There's only one dash in -version

```
java -version
```

I dunno about the rest of your troubles, sorry.

---

### Post by drmrgd on 2012-11-15
> **jim_deadlock said:**
> There's only one dash in -version

```
java -version
```

I dunno about the rest of your troubles, sorry.

This totally ticks me off!  I make this mistake all of the time because I think update-alternatives is the only program that does not use a double-hyphen for the long-name options (well, maybe not the only one...but certainly one of the few!).  Anyway, rant over :D

To the OP:

> Also, if I run a shell file containing the line java -jar someprogram.jar that to run a java app, it does not work. And yet if I type into the terminal

What does this mean?  What is the error you get?  Is it possible that the script is looking in the wrong place for the java executable and that's why you get an error?  

> Also - and even more frustrating...I was trying to run my son's game of minecraft (which is written in java) just to see if another java app would ran. It worked perfectly. Then - and don't ask - I accidentally deleted that icon from "Docky". When I restored it from the trash can, it appeared on the Desktop, and I dragged it back to Docky.

And NOW I am getting a corrupt jar file message when I try and run minecraft, either from the resurrected Docky icon, or from the terminal. But NOTHING was changed, aside from restoring it from trash!?

I'm not sure what this error is.  However, I'll bet it's not due to a java problem, but due to something being off with the launcher.  Can you just create a new launcher, making sure it points to the correct .jar file?

[QUOTE]Any ideas? Many thanks in advance.

(Oh yeah...something else...when I type 
```

update-java-alternatives -l
```
it doesn't even list anything from Sun, just the openJDK 6 and 7.

Unless i missed something, in your update-alternatives query above, there is only openJDK versions of java listed.  I don't see any Oracle versions.  I think this is OK.

---

### Post by SantaFe on 2012-11-15
Here's a link that tells how to add Oracle Java to your Ubuntu O/S: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")  It worked for me in Xubuntu, so Ubuntu shouldn't be a problem. ;)

And here's a link to Verify your Java version: [http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")

---

### Post by BurnDownTheSky on 2012-11-15
> This totally ticks me off!  I make this mistake all of the time because I  think update-alternatives is the only program that does not use a  double-hyphen for the long-name options (well, maybe not the only  one...but certainly one of the few!).  Anyway, rant overWell, I'm glad to know I'm apparently not the only one to make this mistake...although I decided to humiliate myself publicly on such a silly mistake.  :)  Yes indeed, when I use only one hyphen my computer now admits to having a version of java running.  Thanks for pointing that out.

> 
     Quote:
                                                 Also, if I run a shell file containing the line java -jar  someprogram.jar that to run a java app, it does not work. And yet if I  type into the terminal                                 
What does this mean?  What is the error you get?  Is it possible  that the script is looking in the wrong place for the java executable  and that's why you get an error?  Sorry to be unclear.  Ok, the shell file is really simple:

```
#!/bin/sh
java -jar RosterEditor.jar
/bin/bash
```When I run it (and it is marked as executable) it just dies without a sound.  No error messages at all.  (I put the final line in there to keep the terminal window open).  The shell file is in the same directory as the  RosterEditor.jar.

Now, when I open a terminal, and go to that same directory, and type in  java -jar RosterEditor.jar, it works!  This behaviour only started AFTER I ran "update-alternatives --config java"  Before I did that, the shell file worked perfectly!

And I've since changed the chosen java back to my original choice to no avail.  The shell file doesn't work; the terminal does.

> I'm not sure what this error is.  However, I'll bet it's not due to a  java problem, but due to something being off with the launcher.  Can you  just create a new launcher, making sure it points to the correct .jar  file?I think you're right, or perhaps something went awry when I restored the launcher from the trash.  I did just make a new launcher, and it seems to work.  At the time I was getting a bit paranoid about java...everything I was doing that was related to java seemed to be going wrong!  

> Unless i missed something, in your update-alternatives query above,  there is only openJDK versions of java listed.  I don't see any Oracle  versions.  I think this is OK.     Ah, again I wasn't completely clear.  When I run 

```
sudo update-alternatives --config java                                                

There are 3 choices for the alternative java (providing /usr/bin/java).                                                              
                                                                                                                                     
  Selection    Path                                           Priority   Status                                                      
------------------------------------------------------------                                                                         
  0            /opt/java/32/jre1.6.0_30/bin/java               2000      auto mode
  1            /opt/java/32/jre1.6.0_30/bin/java               2000      manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
* 3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

```I get three versions, Oracle being one.

When I run

```
update-java-alternatives -l
java-1.6.0-openjdk-i386 1061 /usr/lib/jvm/java-1.6.0-openjdk-i386
java-1.7.0-openjdk-i386 1051 /usr/lib/jvm/java-1.7.0-openjdk-i386

```I only get the OpenJDK versions.  Shouldn't the jre1.6.0_30 be listed as well?

Again, thanks for all the help, and sorry for any confusion from my poor explanations.

---

### Post by BurnDownTheSky on 2012-11-15
> **SantaFe said:**
> Here's a link that tells how to add Oracle Java to your Ubuntu O/S: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)  It worked for me in Xubuntu, so Ubuntu shouldn't be a problem. ;)

And here's a link to Verify your Java version: [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

Given the luck I seem to be having with Java lately, I'm a bit hesitant to try adding yet another version of java on my computer!  :)  That being said, thanks for the link.  I probably will be installing it in the near future.

I did try the other link, but it claimed I did not have java installed on my system.  I suspect that is because I am currently running OpenJDK and IcedTea.  My browser does run Java applets ([http://www.gamesbreak.com/warzone3-ww2b.html](http://www.gamesbreak.com/warzone3-ww2b.html))

---


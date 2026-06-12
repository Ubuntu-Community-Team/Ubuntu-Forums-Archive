---
title: "Limewire/Frostwire won't run - again!"
date: 2007-06-01
forum: General Help
---

### Post by lbriner on 2007-06-01
I've already trawled the forums for this particular problem and none of the previous postings has fixed it. I am running kubuntu 7.04? - pretty much the latest and I downloaded Limewire (latest from limewire site) and Frostwire 4.13.1 and both fail to run up with the same symptoms.
If I run them, the splash screen appears and then it dies with the following console output:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
/usr/lib/frostwire/runFrostwire.sh: line 122: 12074 Segmentation fault      (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

I have removed all java runtimes except the Sun 1.6 one (as previously suggested). I have added the shell command into /usr/lib/LimeWire/runLime.sh to limit the stack size to 2Mb (ulimit -s 2048 ) which previous posts said might help.

All other people on previous posts say that the things I have tried have fixed their programs but I am at a loss. I can run another Java program successfully that uses windows (another possible issue with Lime/FrostWire is that the window bit causes the problems) Please help.

---

### Post by Gruss2 on 2007-06-02
Hello, I'm having similar issues and I hope some can helps us out!....Frostwire no longer starts even though it has before...and Iriverter, a video converter, is also no longer starting. I wish SOMEONE knowledgeable out there would help us with our issues. It seems this is an issue involving Ubuntu's Fiesty and how it handles Java, but we need Ubuntu's top technicians to help us out here with solutions!

---

### Post by Jay11 on 2007-06-08
This is my first post so i hope it helps. The problem seems to be how fiesty installs java. 
First, run this command in a terminal to get java 6; 
sudo apt-get install sun-java6-jre sun-java6-plugin

Now you have to replace your old java with the new;
sudo update-java-alternatives -s java-6-sun

Next you need to let your system know to use the new java;
sudo gedit /etc/jvm

Then copy and paste this above /usr/lib/jvm/java-gcj or whatever your systems first line is;
/usr/lib/jvm/java-6-sun

Now do 1 last command and see if it worked;
java -version

If it did then Frostwire should work fine now....This is an Azureus fix also though you may have to reinstall Azureus after you do this to get it to work, but Frostwire should be fine :)

I just noticed you seem to have java 6 installed correctly....try uninstalling frostwire, going through these steps, and reinstalling.

---

### Post by Gruss2 on 2007-06-09
Thanks Jay!  It worked!  :D

---

### Post by dj1120 on 2007-06-09
This worked for me too!! Thanks

---

### Post by wulfhound on 2007-06-13
Thanks! This got my Frostwire working, unlike some "how to upgrade/install java" threads I won't mention...

Maybe a rename of the post would be better? 

Sandaili

---

### Post by Jay11 on 2007-06-14
Good to hear im not completely useless ;)

---


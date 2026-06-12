---
title: "frostwire"
date: 2007-12-31
forum: General Help
---

### Post by krysia on 2007-12-31
i have just installed ubuntu ultimate and i can't get frostwire to work it downloads but will not open.
in had no trouble with ubuntu 7.10 so why should ultimate be awkward,other than the frostwire problem i am very pleased with ultimte.
happy new year everyone and i look forward to any help.
krysia

---

### Post by go_beep_yourself on 2007-12-31
What is Ubuntu Ultimate? Why is it named similar to Vista Ultimate?

For frostwire, you need Java.

```
sudo apt-get install sun-java6-jre
```

You might also need to do this too, so that Sun Java gets used instead of GNU Java that comes with Ubuntu by default. These directions are a little old, but you should be able to tweak them a bit to work for your system and your version of java.

> Selecting the default Java version

If you want to use Sun's Java instead of the open source GIJ (GNU Java bytecode interpreter) you need to set it as default. To list installed JVMs:

update-java-alternatives -l

To select, for example, Sun's JVM as provided in Ubuntu 6.06, run:

sudo update-java-alternatives -s java-1.5.0-sun

You should also edit /etc/jvm and move /usr/lib/jvm/java-1.5.0-sun to the top of JVMs offered. 

---

### Post by docorange on 2007-12-31
I think you should run frostwire from the terminal, it will tell you what's wrong...
docorange

---

### Post by krysia on 2007-12-31
thanks have downloaded the java6 and will nbe trying it out later.
krysia

---

### Post by MikeSz on 2008-01-03
sorry to interrupt the thread but im having the same prob.  Had Frostwire working in 7.04 but cant get it working in 7.10 (though I am now on the 64 bit version).  Ive installed the latest java as per the above command and when I try to run from the terminal I get this...

zer0cool@zer0cool-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ad418e9ee25, pid=6098, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid6098.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  6098 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

zer0cool@zer0cool-laptop:~$ 


Any ideas?

---

### Post by Ahslan on 2008-01-04
thx a alot go_beep_yourself...i already had java installed but not that i moved it to the top of the list in the jvm file....it works perfectly now :) THX A LOT!

---

### Post by go_beep_yourself on 2008-01-04
You're welcome. Don't forget to click the thanks button near my post.

---

### Post by MikeSz on 2008-01-06
mines still broke :confused:

I installed Java 6 by copying and pasting command above, then I tried to move it to the top of the list but heres what I got!....

This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

Any ideas why its broke?

---

### Post by go_beep_yourself on 2008-01-07
> **MikeSz said:**
> mines still broke :confused:

I installed Java 6 by copying and pasting command above, then I tried to move it to the top of the list but heres what I got!....

This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

Any ideas why its broke?

I see you are using 64 bit. Are you trying to get java working in your web browser or for Frostwire? You ought to be asking in the 64 bit part of the forum. Since java is a 32 bit application only, you may run into a few problems with it, but nothing that can't be solved. I use 32 bit swiftweasle for websites with java. In your case, you need to do these commands.

sudo apt-get install ia32-sun-java6-bin ia32-libs
sudo update-alternatives --config java

Then choose the ia32 version of Java 6.

---

### Post by MikeSz on 2008-01-07
Many thanks indeed - was just trying to get it working for Frostwire and that has worked a treat.  Didnt realise there was a 64 bit forum so will use that next time - just thought since I have the amd64, might as well give the 64 bit version a try.  Many thanks again for your help

---


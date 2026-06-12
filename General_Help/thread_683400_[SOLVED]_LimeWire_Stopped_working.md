---
title: "[SOLVED] LimeWire Stopped working"
date: 2008-01-30
forum: General Help
---

### Post by locky28 on 2008-01-30
Hi All,

Not sure if this is in the right place but here goes anyway.

I Installed limewire quite some time ago and after I got around the compizfusion problem by installing a newer version of Java it worked fine for months.

However one day it just stopped working. The hard drive on my lappy would thrash for a bit but nothing would happen so I tried running it through terminal and got this...

```
#
locky@locky1:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading LimeWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b729e689e11, pid=7798, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid7798.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
./runLime.sh: line 124:  7798 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)

locky@locky1:~$ 


```

I tried re-installing all the Java looking stuff using synaptic but I must admit I was pretty much flying blind.

I would really appreciate some help.


Thanks for your help,

Locky.

---

### Post by CupofDice on 2008-01-30
First, type in the terminal.

sudo update-alternatives --config java

If it only gives you icetead and gij as options, then type-

sudo apt-get install sun-java6-bin sun-java6-jre

Then once again in the terminal type 

sudo update-alternatives --config java

and choose the sun java version you just installed.

---

### Post by orbish on 2008-01-31
A quick fix would to be using frostwire

sudo apt-get install frostwire

---

### Post by locky28 on 2008-01-31
Thanks CupofDice that worked a treat, Java 6 was the winner.

Thanks orbish, I was going to give your suggestion a go if I couldn't get the limewire I'm used to working, but looks like it's all worked out.


Thanks again.

---


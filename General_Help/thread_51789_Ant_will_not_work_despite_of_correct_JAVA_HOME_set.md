---
title: "Ant will not work despite of correct JAVA_HOME settings"
date: 2005-07-25
forum: General Help
---

### Post by Gnurou on 2005-07-25
Hi everyone,

I'm a little bit desperate on this one, since I've been search for hours now.

I have sun-j2sdk1.5 installed from ubuntu-backports, as well as ant 1.6.2 from universe. Problem is, when i try to compile my project, I get the following error:

BUILD FAILED
/home1/gnurou/Work/JITS/build.xml:143: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK

The message is rather clear - so I've set up JAVA_HOME correctly:

$ echo $JAVA_HOME
/usr/lib/j2sdk1.5-sun/

$ ls $JAVA_HOME/lib/
dt.jar  htmlconverter.jar  ir.idl  jconsole.jar  orb.idl  sa-jdi.jar  tools.jar

Unfortunately, I still get the same error. Note that if JAVA_HOME is wrong, ant fails sooner - otherwise it fails when invoking the javac task.

Everything seems to be correct from what I know. Does anyone have a clue? I'd really appreciate it.

Thanks!
Alex.

---

### Post by Gnurou on 2005-07-25
Eventually I made my own java package using java-package, and replaced ubuntu-backports package by it, and it works. I don't explain it, though.

Sorry, should have tried this before posting.

---


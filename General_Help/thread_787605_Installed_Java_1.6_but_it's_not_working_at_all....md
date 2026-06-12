---
title: "Installed Java 1.6 but it's not working at all..."
date: 2008-05-09
forum: General Help
---

### Post by Moonfrost on 2008-05-09
Well, I was having problems installing Java (as usual after a clean install of Linux) and I decided for the hundredth time to try to install it from the repos using synaptic...well, I tried running Frostwire which is a java progrm, I ran it through command line to see if there was any error to so that I could check the output.

Well here it is, frostwire found the java executable but says that something went wrong and that probably I have the wrong version of Java...hmmm, it says it needs at least Sun Java 1.4+ and then it tells me the version I have is 1.6...ironic huh? can anybody help? oh and by the way, it's not working with Firefox either, what can I do?

Here's the whole output:

```
username@username-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007ff124578755, pid=11705, tid=1107155280
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid11705.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 11705 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)
```

EDIT: I figured that probably there's a problem because I'm using 64bit Java (64bit OS obviously) but I think frostwire is 32bit only...the thing is, I can never install Java from the file you download from the website because somehow it ends up installing on the desktop for some reason because otherwise I could install the 32bit version that way...but the version I get on the repos is only 64bit because I'm running 64bit Hardy...

---

### Post by Thanoulis on 2008-05-09
There is no such thing as Java 64bit...try to install the IcedTea package instead. It is a 64bit open source java environment.

---

### Post by live2learn on 2008-05-09
installing openjdk package will run your software:guitar:

---

### Post by Moonfrost on 2008-05-09
> **live2learn said:**
> installing openjdk package will run your software:guitar:

Already tried that and none of my java software works with it...it has never worked before, I always used sun-java and everything was perfect...

---

### Post by Moonfrost on 2008-05-09
> **Thanoulis said:**
> There is no such thing as Java 64bit...try to install the IcedTea package instead. It is a 64bit open source java environment.

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

---

### Post by descentspb on 2008-05-09
In x64, i've made my Firefox and Opera work **flawlessly** with latest flash and JavaRE just with changing the x64 versions of the browsers to x32 and manually installing flash and java into the corresponding plugin directories of the browsers. I've tried really hard to make Java work with x64 Firefox, tried OpenJDK etc. but id din't help. Just download an x32 version of Firefox and Java, and put the java/plugin/i386/ns7/libjavaplugin_oji.so into firefox/plugins.

P.S. Of course, you should have ia32-libs installed.

---

### Post by Moonfrost on 2008-05-09
> **descentspb said:**
> In x64, i've made my Firefox and Opera work **flawlessly** with latest flash and JavaRE just with changing the x64 versions of the browsers to x32 and manually installing flash and java into the corresponding plugin directories of the browsers. I've tried really hard to make Java work with x64 Firefox, tried OpenJDK etc. but id din't help. Just download an x32 version of Firefox and Java, and put the java/plugin/i386/ns7/libjavaplugin_oji.so into firefox/plugins.

P.S. Of course, you should have ia32-libs installed.

Yeah I thought about that...nothing is perfect on 64bit, oh well I'll have to do just that then...the problem now is that I can't copy any files into those directories because I am not the owner of those and I can't enable the root account anymore because for that I need the Login window option which I have but I need to be running Gnome for that and I'm running KDE 4, I tried running it on Gnome but it tells me that Gnome is not the default DE so I can't run it and when I log in to KDE it doesn't give me the option to set another DE as default...:(

---


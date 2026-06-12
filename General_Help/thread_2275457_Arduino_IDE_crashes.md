---
title: "Arduino IDE crashes"
date: 2015-04-26
forum: General Help
---

### Post by stepheny on 2015-04-26
When I run the Arduino IDE on my 15.04 (and 14.10) 64 bit OS it crashes, with the following report, when I try and save data. It works perfectly on Ubuntu 14.04 32 bit OS. 


```
~$ arduino
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fdf6b0ec70c, pid=6609, tid=140596350019328
#
# JRE version: Java(TM) SE Runtime Environment (8.0_45-b14) (build 1.8.0_45-b14)
# Java VM: Java HotSpot(TM) 64-Bit Server VM (25.45-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libawt_xawt.so+0x4470c]  handle_response+0xac
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6609.log
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
#
/usr/bin/arduino: Zeile 36:  6609 Abgebrochen             (Speicherabzug geschrieben) java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel processing.app.Base "$@"
```

From the internet I have found out that the file  librxtxSerial.so might actually be a 32 bit version and this might be the reason for the crashes. Is this true and if it is where can I gel a 64 bit version of  librxtxSerial.so ?

---

### Post by taniwhaiti on 2015-05-09
I am also seeing this error - since dist upgrade - and i'm on 32bit vivid.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x6222b307, pid=10461, tid=1576397632
#
# JRE version: OpenJDK Runtime Environment (8.0_45-b14) (build 1.8.0_45-internal-b14)
# Java VM: OpenJDK Server VM (25.45-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libawt_xawt.so+0x41307]
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /home/brenda/Downloads/arduino-1.6.4/hs_err_pid10461.log
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.java.com/bugreport/crash.jsp](http://bugreport.java.com/bugreport/crash.jsp)
#
./arduino: line 29: 10461 Aborted                 (core dumped) java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel $SPLASH processing.app.Base --curdir $CURDIR "$@"

---

### Post by m-bachmann on 2015-06-16
There solution is described here:
 [http://forum.arduino.cc/index.php?topic=318520.0](http://forum.arduino.cc/index.php?topic=318520.0)

I've just added the line to the arduino file, now it works again.

---

### Post by taniwhaiti on 2015-06-16
Thanks. that works.

---


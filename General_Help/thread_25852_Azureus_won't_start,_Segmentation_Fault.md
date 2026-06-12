---
title: "Azureus won't start, Segmentation Fault"
date: 2005-04-11
forum: General Help
---

### Post by dabeej on 2005-04-11
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_02]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
./azureus: line 107: 17857 Segmentation fault      ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.


It worked before, then gnome-panel repeatedly crashed, now this! Don't understand. Anyone else has or had this issue? I havent tried reboot. I don't see how that would solve anything.

---

### Post by artinla on 2005-04-11
With Azureus, its all about the JAVA install and environment variables.  I suspect your environment is somehow hosed.  

post the output from the following commands:

$echo $JAVA_HOME

java -version

$echo $PATH


Art

---

### Post by dabeej on 2005-04-11
dabeej@extricate:~$ echo $JAVA_HOME
/usr/java/jre1.5.0_02
dabeej@extricate:~$ java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)
dabeej@extricate:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/java/jre1.5.0_02/bin


What's weird is. I don't see a problem =/ .

---

### Post by dabeej on 2005-04-11
I rebooted. Works. It doesn't make sense to me! Well I guess the problem is solved.  :|  I would like to know what happened.


Thanks.

---

### Post by artinla on 2005-04-11
Great!

I had the same problem, It seems like the trouble had something to do with sudo.  I had to manually update the /etc/bash.bashrc with the proper lines (from the Ubuntu guide). On a related note, I had to install LimeWire as a normal user instead of my habitual sudo in order to get it to work.  I have read where there is a glitch in Thunderbird where you have to run it once as a true "root" before doing anything or it will not work. 

Strange, but I don't care as long as people who are smarter than I have already discovered a workaround.

Good luck,

Art

---


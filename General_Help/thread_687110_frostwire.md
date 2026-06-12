---
title: "frostwire"
date: 2008-02-04
forum: General Help
---

### Post by maphco on 2008-02-04
I installed frostwire, and the dialog box said installation finished, however when I went to use the application it wouldn't load. anyone know what happened?

---

### Post by earobinson on 2008-02-04
try runing it from the terminal and let us know what it outputs (also this is probaly the wrong section for this post)

---

### Post by maphco on 2008-02-04
Sorry, I posted it in the wrong section.

---

### Post by maphco on 2008-02-04
How do I run it from the terminal?

---

### Post by p_quarles on 2008-02-04
Open a terminal and type:
```
frostwire
```

---

### Post by maphco on 2008-02-04
THis is the error section that appeared in the terminal:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b1e027f3e11, pid=32506, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid32506.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 32506 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS

---

### Post by Sproid on 2008-02-04
Got same problem. This could be solve using a previews version of java, but in my ubuntu 64bit the flash player wont work then. so i preferred sacrifice limewire or frostwire, and use ktorrent and amule. If in very need of limewire or frostwire I simply use limewire in Windows on my pc (dualboot). but a solution will be very appreciated, since will be a step in for Linux and far from windows.

---


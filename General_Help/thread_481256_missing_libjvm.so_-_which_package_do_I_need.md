---
title: "missing libjvm.so - which package do I need?"
date: 2007-06-22
forum: General Help
---

### Post by jasonkwan on 2007-06-22
Hello,

I've installed a molecular modelling program using the supplies automatic installer.  This supposedly included jre.  Now when I try to run it I get the following:

jason@jason-desktop:/opt/tinker/bin$ ./pdbxyz -h
./pdbxyz: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory

I used the find command to see if libjvm.so was on my hard disk somewhere, but it isn't.  I've got loads of java-related packages installed so I'm at a loss as to what I'm missing here.  Does anyone know which package contains libjvm.so?

Thanks

Jason Kwan

---

### Post by TalioGladius on 2007-10-04
bump


I'm getting the same message with groupwise

---

### Post by joseelsegundo on 2007-11-26
> **TalioGladius said:**
> bump


I'm getting the same message with groupwise

As far as groupwise goes you will need a 32-bit JRE which is available in Synaptic.  For AMD64 I use ia32-sun-java6-bin, for i386 you can just use the sun-java6-jre.

Next, I wrote a small shell script (my Groupwise install is in /opt):

```

#!/bin/bash
export JRE_HOME=/usr/lib/jvm/ia32-java-6-sun/jre
export LD_LIBRARY_PATH=$JRE_HOME/lib/i386:$JRE_HOME/lib/i386/client:$LD_LIBRARY_PATH
/opt/novell/groupwise/client/bin/groupwise "$@" &

```

I put that script in the same directory as the Groupwise binary.

Running that script should bring Groupwise up.

Groupwise seems to still keep a process running after you quit so you'll want to kill that when you quit.  I added a ```
killall -s 9 groupwise
``` in the script just before running groupwise to kill any existing Groupwise instances.

---


---
title: "Opera Errors with Java"
date: 2005-09-22
forum: General Help
---

### Post by zorak on 2005-09-22
I just installed Opera 8.5 on my Ubuntu 5.04 PC. When i start Opera i get this message.

```
opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       Start Opera with '-debugjava' argument for more information.
```

So as suggested in the error i ran Opera -debugjava, this is the output.

```
opera: [java] There seems to be a preloaded version of Xt.
       There is a workaround for this problem in the opera
       startup script.  If that workaround fails, opera will
       most likely crash every time it tries to use Java.
       The workaround seems to have failed.  Java will be disabled.
       Technical explanation:
       There is a problem with the order of loading Xt and
       Java.  If Xt is loaded before libawt (part of Java),
       Java will crash when it tries to access the screen.
       The workaround is based on using LD_PRELOAD to load
       libawt.so first.

opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       The actual problems should be described above.
```

this is the output of Java -version

```
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)
```

I installed Java through apt-get.

Anyone have any suggestions on how to correct this error?

---

### Post by zorak on 2005-09-22
Fixed.

For me it was an issue with the Java path. (funny that the error message could'nt just say "invalid path"   :roll: ) 

In case someone else runs into this problem. Here is how I fixed it.

Open Opera, Press F12 and select "Enable Java". Then Goto Tools --> Preferances, Click on the Advanced Tab. Click on Content, then the Java Options button. Then Input your correct path, for me the path was "/usr/lib/j2re1.5-sun/lib/i386/" from what i read that may be differant between distros.

---

### Post by berserker on 2005-09-25
Thank you!  I had the same problem and your solution worked for me as well.

---

### Post by Hairy_Palms on 2005-09-25
now if only opera supported the acrobat reader and mplayer plugins >.<

---


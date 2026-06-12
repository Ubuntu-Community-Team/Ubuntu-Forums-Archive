---
title: "Java Virtual Machine in Lubuntu"
date: 2018-04-30
forum: General Help
---

### Post by t0p on 2018-04-30
I am running lubuntu 17.10.1 32-bit in VirtualBox.  I want to run ZAP_2_7_0, but when I tried I got this:
```

t0p@lubu:/media/sf_Lubu$ ./ZAP_2_7_0_unix.sh 
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.8.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
t0p@lubu:/media/sf_Lubu$ 

```

Is there no JVM installed by default in Lubuntu?  If not, what should I install?  I looked in the Software thing, but am no wiser (I haven't used Linux for a while, and I miss Synaptic :( ) And how do I perform the command "define INSTALL4J_JAVA_HOME to point to a suitable JVM"?

Cheers.

---

### Post by ajgreeny on 2018-04-30
Try installing **uwsgi-plugin-jvm-openjdk-8** from the repos which sounds as if it may be what you need.

I have no real experience of java VMs so could easily be wrong and have no knowledge of ZAP, but it must be worth a try.

While doing so you can also install synaptic, though I believe it is already in Lubuntu which I am using to write this and I don't think I had to install it, so you may have simply missed it when searching the menu.

---


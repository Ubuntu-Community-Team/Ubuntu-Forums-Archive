---
title: "Java Problem"
date: 2007-04-19
forum: General Help
---

### Post by Clay_Banger on 2007-04-19
Hi all.
i have a java program that runs fine on gentoo linux, but doesnt run on (k,x)ubuntu. The command to start the program from the command line is:
```
java -jar new-bt.jar
```
but whenever I do that i get this error:
```
Starting bluetooth node server...
Using Device #0
Could not find own library libavetanaBT.so. Will try from ld.library.path
Exception in thread "main" java.lang.UnsatisfiedLinkError: no libavetanaBT.so in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at com.pracucci.jbluetooth.util.LibLoader.loadLib(LibLoader.java:142)
        at com.pracucci.jbluetooth.util.LibLoader.loadBTLib(LibLoader.java:50)
        at com.pracucci.jbluetooth.stack.BlueZ.<clinit>(BlueZ.java:93)
        at com.pracucci.jbluetooth.stack.BluezProtocolStack.<init>(BluezProtocolStack.java:66)
        at javax.bluetooth.LocalDevice.<init>(LocalDevice.java:88)
        at javax.bluetooth.LocalDevice.getLocalDevice(LocalDevice.java:132)
        at com.kukanstudio.podmo.node.NodeServer.main(NodeServer.java:37)
```
I have all of the required dependences of the program installed and i have tried various versions of the java program. the file that it refers to(libavetanaBT.so) is in the new-bt.jar
any ideas?

---


---
title: "java problem with an application"
date: 2007-03-04
forum: General Help
---

### Post by dschaefer79 on 2007-03-04
Hello,

I've tried to install my e-banking application for linux and I get this error message when launching. It's a java 1.4 application and java is integrated with the application

Can anyone help me thanks. 

sh$ ./e-banking_linux_fr.bin 

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:140)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
        at java.awt.Window.init(Window.java:224)
        at java.awt.Window.<init>(Window.java:268)
        at java.awt.Frame.<init>(Frame.java:398)
        at java.awt.Frame.<init>(Frame.java:363)
        at com.zerog.ia.installer.Main.c(Unknown Source)
        at com.zerog.ia.installer.Main.main(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at com.zerog.lax.LAX.launch(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
GUI-

---


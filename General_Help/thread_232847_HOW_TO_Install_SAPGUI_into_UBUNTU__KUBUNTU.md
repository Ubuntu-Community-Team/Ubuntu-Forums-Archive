---
title: "HOW TO Install SAPGUI into UBUNTU / KUBUNTU"
date: 2006-08-09
forum: General Help
---

### Post by fedemw on 2006-08-09
Hi all,
 
I make this manual for people who need install SAPGUI for Linux.

1) 

Minimal system requeriments.

Linux
Hardware:
CPU: Intel PentiumIII with 800 MHz
RAM: 256MB
Software:
OS: SuSE Linux 9.3 - 10.1, Red Hat Enterprise Linux 3 and 4
JVM: Sun Java Runtime Evironment 1.4.2 (32-bit) or 5.0 (32-bit) including Java Plugin
please see [http://java.sun.com/j2se/1.4.2/install-linux.html](http://java.sun.com/j2se/1.4.2/install-linux.html) and [http://java.sun.com/j2se/1.4.2/docs/guide/intl/locale.doc.html](http://java.sun.com/j2se/1.4.2/docs/guide/intl/locale.doc.html) resp. [http://java.sun.com/j2se/1.5.0/install-linux.html](http://java.sun.com/j2se/1.5.0/install-linux.html) and [http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html](http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html) for details


2) 

Download SAPGUI from: 

[ftp://ftp.sap.com/pub/sapgui/java/](ftp://ftp.sap.com/pub/sapgui/java/)
(anonymous login)

[https://websmp201.sap-ag.de/sapgui-java](https://websmp201.sap-ag.de/sapgui-java)
(OSS user and pass)


3)

At /java folder in ftp select:


File: PlatinGUI-Linux-700.jar 	37926 KB 	11/07/06 	13:58:00


(note: maybe a new version is available)

4)

At downloaded folder, execute

java -jar PlatinGUI-Linux-700.jar

5) Executing SAPGUI

A) Guilogon:

~/SAPClients/SAPGUI7.00/bin$ ./guilogon

To create servers, touch at new and go to "advanced".

-- tip “use expert configuration”

Example:

For server 10.1.1.6 with system number 01:

conn=/H/10.1.1.6/S/3201


B) Command line

For server 10.1.1.6 with system number 01:

~/SAPClients/SAPGUI7.00/bin$ ./sapgui /H/10.1.1.6/S/3201


Hope it helps, Goodbye!

---

### Post by vgeneral on 2006-09-24
I'm trying to install the SAPGUI interface onto my Ubuntu 6.06 system but am having issues with the installation.  I tried running the java command,
java -jar PlatinGUI-Linux-700r1.jar, and recieved the following message:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.sap.platin.base.install.GuiInstall.main(GuiInstall.java:460)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more

It seems to me that the installation failed, based on the "...AWTError: Cannot load AWT toolkit..." message above.  I'm running the following version of java (which was installed through the add/remove applications utility)
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Any help would be greatly appreciated.

---

### Post by lamego on 2006-09-24
It seems you need gtk bindings for java:
```
sudo apt-get install libgtk-java libswt3.1-gtk-java
```

---

### Post by vgeneral on 2006-09-24
I solved my issue by using what was suggested in the thread listed below.

[http://www.ubuntuforums.org/showthread.php?t=232711&highlight=load+AWT+toolkit%3A](http://www.ubuntuforums.org/showthread.php?t=232711&highlight=load+AWT+toolkit%3A)

I ran sudo update-alternatives --config java and chose the java option to complete the installation.

---

### Post by s4ncho on 2007-01-17
> **fedemw said:**
> 
A) Guilogon:

~/SAPClients/SAPGUI7.00/bin$ ./guilogon

To create servers, touch at new and go to "advanced".

-- tip “use expert configuration”

Example:

For server 10.1.1.6 with system number 01:

conn=/H/10.1.1.6/S/3201


B) Command line

For server 10.1.1.6 with system number 01:

~/SAPClients/SAPGUI7.00/bin$ ./sapgui /H/10.1.1.6/S/3201


Hope it helps, Goodbye!
but how can i connect to existing server?

i was told to type in sapgui (sapgui for ms) : > description: University
app's server: 192.168.1.1
sap router: /H/166.17.89.195/H  
system ID: R3I
system number: 20
system: R/3//hope my translation is ok.

above i've changed the address, in security reason

how linux expert configuration should look for something like that??

i've copied my friend's sapgui ms configuration (saplogon.ini) 
& have entered its location in the guilogon - but with no luck :(

---

### Post by vbvamsi on 2007-09-21
Hi fedemw,

I used the above steps and was able to install SAP Gui successfully on my Feisty on AMD 64.

I still have a problem getting the resolution of the screen to work. My computer has a 1280X800 screen. SAP can only use a part of the screen, remaining is just white screen. Could you please help me to fix this.

Thanks

---

### Post by skabuby on 2007-12-05
Hi,
  I follow the step mentioned above but I still have this error:

[I]java -jar /home/skabuby/PlatinGUI-Linux-710.jar 
Exception in thread "main" java.lang.UnsupportedClassVersionError: com/sap/platin/micro/Microkernel (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)[/I]


Any suggestions???
Thankx, skabuby

---

### Post by skabuby on 2007-12-05
> **skabuby said:**
> Hi,
  I follow the step mentioned above but I still have this error:

[I]java -jar /home/skabuby/PlatinGUI-Linux-710.jar 
Exception in thread "main" java.lang.UnsupportedClassVersionError: com/sap/platin/micro/Microkernel (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)[/I]


Any suggestions???
Thankx, skabuby

I've solved this problem. It was because I installed wrong SDK version. With 6 everything ok!
Bye, Skabuby

---


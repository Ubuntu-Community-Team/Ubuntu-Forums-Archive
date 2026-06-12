---
title: "Azureus problem x86_64"
date: 2005-03-26
forum: General Help
---

### Post by krusk on 2005-03-26
Hey

I've got this strange problem with azureus. I've installed sun jre 1.5.0_02, the newest jre. And after extracting azureus and trying to execute it, it gives me this error:

> rasmus@ubuntumus:~$ /home/rasmus/programmer/azureus/./azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/java/jre1.5.0_02/bin/
OOPS, you don't seem to have a valid JRE  [/usr/java/jre1.5.0_02/bin/java = Error]
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
rasmus@ubuntumus:~$ 

After reinstalling both java and azureus several times, i have no clues...

In my opinion, it looks like a problem with azureus, not jre (which installs fine).


Any ideas?  :roll:

---

### Post by zarathustra on 2005-03-26
> /usr/java/jre1.5.0_02/bin/java -Xms16m -Xmx128m -cp "/home/nick/azureus/Azureus2.jar:/home/nick/azureus/swt.jar:/home/nick/azureus/swt-mozilla.jar:/home/nick/azureus/swt-pi.jar" -Djava.library.path="/home/nick/azureus" -Dazureus.install.path="/home/nick/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/nick/azureus/libswt-pi-gtk-3106.so: /home/nick/azureus/libswt-pi-gtk-3106.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:100)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:118)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:71)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:55)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:106)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:73)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:100)
Azureus TERMINATED.


This is what I get when trying to run it. What have I done wrong?

---

### Post by jdong on 2005-03-26
You don't have libswt-pi-gtk.... Check Azureus's website for what dependencies it has, and make sure you satisfy them all manually before trying to start Azureus.

---

### Post by zarathustra on 2005-03-27
I have followed what it says on Azureus's website, and downloaded a zip file with required files and extracted to Azureus's folder. But it still does not work.

---

### Post by cdhotfire on 2005-03-27
do
```

java -version

```
just to make sure java is installed.

---

### Post by zarathustra on 2005-03-27
> nick@ubuntu:~$ java -version
gij (GNU libgcj) version 3.4.4 20050209 (prerelease) (Debian 3.4.3-9ubuntu3)

Copyright (C) 2002 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Is what I got back...

---

### Post by cdhotfire on 2005-03-27
do this:
Download JRE: [Here]("http://java.sun.com/j2se/1.5.0/download.jsp")
     cd browse_to_your_download_folder
```

sh jre-1_5_0_02-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_02/ /usr/java/
sudo chown -R root:root /usr/java/jre1.5.0_02/
sudo ln -s /usr/java/jre1.5.0_02/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_02/bin/java_vm /usr/bin/java_vm
sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
sudo gedit /etc/bash.bashrc

```

Add this at the end
```

     JAVA_HOME=/usr/java/jre1.5.0_01
     export JAVA_HOME
     PATH=$PATH:$JAVA_HOME/bin
     export PATH

```

then try java -version again and that should work.
:)

---

### Post by zarathustra on 2005-03-27
Still comes up with the same message :(

---

### Post by cdhotfire on 2005-03-27
hmm. Seems you installed it from Synaptic correct?

Go to synaptic and remove it.  Then do what i said before and try java -version. Hopefully this will work.;)

---

### Post by zarathustra on 2005-03-27
OK Java is installed properly now!

---

### Post by cdhotfire on 2005-03-27
[QUOTE=zarathustra]OK Java is installed properly now![/QUOTE]

did what i say work?, for future reference.

---

### Post by zarathustra on 2005-03-27
Many thanks! :)

I still have my Azureus problem though :(

---

### Post by cdhotfire on 2005-03-27
[QUOTE=zarathustra]Many thanks! :)

I still have my Azureus problem though :([/QUOTE]

I have no idea.8-[. Maybe someone else can help, if java works azureus should work.

---

### Post by zarathustra on 2005-03-29
Managed to get it working, had the wrong version of Java installed  :oops:

---


---
title: "Frostwire Problems"
date: 2007-10-29
forum: General Help
---

### Post by Kaji on 2007-10-29
I searched around, and couldn't find any solutions that solved my problem.

But I just installed frostwire tonight, and i tried to open it. It wouldn't do a darn thing.

Here is what I get when I do frostwire in terminal:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)


```

Anyone have solutions?

Thanks in Advance.

---

### Post by Crafty Kisses on 2007-10-29
> **Kaji said:**
> I searched around, and couldn't find any solutions that solved my problem.

But I just installed frostwire tonight, and i tried to open it. It wouldn't do a darn thing.

Here is what I get when I do frostwire in terminal:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)


```

Anyone have solutions?

Thanks in Advance.
Do you have Java installed?

---

### Post by Kaji on 2007-10-29
Yes, I believe I have java installed. Any links or directions for where I can install Java, incase i missed it?

---

### Post by Maestro23 on 2007-10-29
> **Kaji said:**
> Yes, I believe I have java installed. Any links or directions for where I can install Java, incase i missed it?

Open a terminal:

> java -version

Tell you if its installed and the version.

---

### Post by Kaji on 2007-10-29
> **Maestro23 said:**
> Open a terminal:



Tell you if its installed and the version.



The outcome of java -version is:

```
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

```

Any help?

---

### Post by rsambuca on 2007-10-29
Frostwire needs the ia32 version of java.  Try installing```
sudo apt-get install ia32-sun-java6-bin
```, and then switching to that version of java before opening frostwire.

---

### Post by Spike-X on 2007-11-03
> **rsambuca said:**
> Frostwire needs the ia32 version of java.  Try installing```
sudo apt-get install ia32-sun-java6-bin
```, and then switching to that version of java before opening frostwire.

This finally got it working for me, thanks!

---

### Post by FearBefore28 on 2008-03-21
I hate to revive a dead thread but i'm having this same issue, when I check my java version i get

java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
spencer@spencer-laptop:~$ 

and then when i try and install the ia32 version i get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package ia32-sun-java6-bin has no installation candidate

can anyone give me a hand?

---

### Post by ubuntu27 on 2008-03-22
> **FearBefore28 said:**
> 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package ia32-sun-java6-bin has no installation candidate

can anyone give me a hand?

Check out the[ Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page


Summary

```
sudo apt-get install ubuntu-restricted-extras
```

That command will install Java, Flash player, and some multimedia codecs (mp3, etc)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install DVD support:

```
sudo apt-get install libdvdcss2
```

Install the rest of the multimedia codecs. Do ONE of the following

**If you are using i386 (32bit Sy**stem)

```
sudo apt-get install w32codecs
```

**If you are using amd64 **(64bit System, it includes Intel 64bit)

```
sudo apt-get install w64codecs
```

---

### Post by MikeSz on 2008-04-08
> **rsambuca said:**
> Frostwire needs the ia32 version of java.  Try installing```
sudo apt-get install ia32-sun-java6-bin
```, and then switching to that version of java before opening frostwire.

Can I please ask how you switch versions?  Ive installed ia32-sun-java6 but frostwire is still looking at the old version for some reason

---

### Post by rsambuca on 2008-04-08
> **MikeSz said:**
> Can I please ask how you switch versions?  Ive installed ia32-sun-java6 but frostwire is still looking at the old version for some reason

If you run the following command, you can select the ia32 java from the list:

```
sudo update-alternatives --config java
```

---

### Post by MikeSz on 2008-04-08
cheers, got it.

---

### Post by marfal on 2008-06-08
I've had problems getting Frostwire to run on Hardy, worked fine with gutsy.
My problems were solved by uninstalling "openjdk-6-jre" with synaptic package manager.
java 1.6 was already installed previously.

all worked fine after that.

Hope this helps.

---

### Post by navneetb1050 on 2008-07-23
Dudes. If your going to download mp3's the best thing to do is download them from google. I tried frostwire but the thing won't work no matter what i do. Go to google type in intitle:"index.of"(MP3)______(whatever song), find your song, right click, save target..and Tada!. Gotcha mp3's.

---

### Post by ubuntu27 on 2008-07-23
I go to the legal and fast way:

Buy and Download MP3 WITHOUT DRM :)  at [Amazon.com]("http://www.amazon.com/exec/obidos/tg/browse/-/163856011/ref=topnav_storetab_dmusic")

---


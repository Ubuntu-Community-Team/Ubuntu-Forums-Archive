---
title: "cant install program (sh file) ubuntu 12.04"
date: 2018-10-18
forum: General Help
---

### Post by juzek on 2018-10-18
Hello i have an issue with tmolex installation, when i want to give permission to sh file i cannot do it, it says there is no such file, also when i want to execute it there is the same
information. I tried ealrier installing this program, something went wrong and i got into login loop, changing owner of xauthority helped fixing that login problem but the program tmolex is not working,
there is icon of the program and when i click on it nothing happens, in installed programs it is now showed, the first crash was when i the program was installing x server and openbox.  Anyone could help with that installation process?


this is error log from the folder when program files are.

```
java.lang.UnsatisfiedLinkError: /home/piotrek/COSMOlogic11/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at sun.security.action.LoadLibraryAction.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Unknown Source)
    at java.awt.Toolkit.<clinit>(Unknown Source)
    at java.awt.Color.<clinit>(Unknown Source)
    at de.cosmologic.tmolex.TmoleX.<clinit>(TmoleX.java:30)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
    at com.install4j.runtime.launcher.Launcher.main(Unknown Source)
java.lang.UnsatisfiedLinkError: /home/piotrek/COSMOlogic11/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at sun.security.action.LoadLibraryAction.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
    at sun.awt.DebugHelper.<clinit>(Unknown Source)
    at java.awt.Component.<clinit>(Unknown Source)
    at com.exe4j.runtime.LauncherEngine.handleFailure(Unknown Source)
    at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
    at com.install4j.runtime.launcher.Launcher.main(Unknown Source)
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class com.exe4j.runtime.util.InternalErrorFrame
    at com.exe4j.runtime.LauncherEngine.handleFailure(Unknown Source)
    at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
    at com.install4j.runtime.launcher.Launcher.main(Unknown Source)
```

---

### Post by TheFu on 2018-10-18
Support for 12.04 ended in 2017.  Being on a supported release is important.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The script seems to be a wrapper around Java.

---

### Post by juzek on 2018-10-18
Someone from office told me to run that programy only on ubuntu 12.04, but on manual of the program it says kernel 2.6.x or newer, so i guess it should be working for example on a 14.04 or 16.045 which are supported ?!
is there a way to solve java issue on this 12.04 ? and he updated kernel to 3.13 but didint go for 14.04 version.

---

### Post by TheFu on 2018-10-18
The forum rules don't allow support for unsupported releases. Sorry.  Nobody here works for Canonical. We are just volunteers.

I did google for something to help, but tmolex seems to be very specialized and well outside my knowledge.

It is possible for a corporate customer to pay Canonical for extra support with 12.04.  I don't think it is cheap and I have no idea what the terms might be or whether java would be included in that support.  Update: [https://buy.ubuntu.com/](https://buy.ubuntu.com/) says US$150 for a desktop per year.  Servers are more. Canonical requires at least US$2500 to be spent to get any level of support according to that page.

14.04 support will end April 2019, so in 6 months. Not worth your time, IMHO.

16.04 support ends April 2021, so that would be a viable option.  Most of my systems are on 16.04.5 still with no plans to migrate for at least a few more years.

18.04 support ends April 2023, but it is very new and there seem to be many unsolved issues with it.  I don't run 18.04 and will be holding off at least a few more months, probably longer.

Today, if I had to deploy a fresh desktop, laptop, or server, I'd use 16.04.5, but other people have different needs. Only you can make the best decision for your situation.

---

### Post by sp40140 on 2018-10-18
Looks like it can't find one file: "/home/piotrek/COSMOlogic11/jre/lib/i386/xawt/libmawt.so: libXext.so.6".
Can you navigate to the path and make sure the file is there?

---

### Post by juzek on 2018-10-18
im gonna check it, and maybe install 16.04 supported version of ubuntu,  since manual of the desired programm says it can run on kernel 2.6.x or  newer.
Also when i try to install tho midnight commander that file i  can see "Could not display the GUI. This application needs access to an X  Server"

---


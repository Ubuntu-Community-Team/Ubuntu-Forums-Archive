---
title: "problems installing staroffice"
date: 2007-02-11
forum: General Help
---

### Post by seshomaru samma on 2007-02-11
i downloaded the 3 months trial version of star office but when i run it i get a series of errors :
```
sesho@laptop:~/Desktop$ sh so-8-pp5-eval-bin-linux-en-US.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice]
/var/tmp/lasttry_staroffice
File is being checked for errors ...
Unpacking ...
All files have been successfully unpacked.
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
InvocationTargetException in ArchiveReader constructornull
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        ... 7 more
Target Exception Trace:
java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)

```

can anyone help me?

---

### Post by ndefontenay on 2007-02-11
Might not be that at all, but have you installed Java yet?

It looks like it's pretty needed here.

---

### Post by seshomaru samma on 2007-02-12
I have Java Runtime Environment installed if thats what you mean
BTW - in Sun's website the only system requirements they had is a relatively new kernel and glib, nothing about Java....

---

### Post by drpaul on 2007-02-13
Why not use OpenOffice? It's in the repos.

Paul

---

### Post by seshomaru samma on 2007-02-13
Open Office lacks one function that I need for school
I'm talking about being able to view embedded comments written in  MS Office
I believe Star Office can do it

---


---
title: "Grammar Extension Manager"
date: 2016-02-18
forum: General Help
---

### Post by TWFJR on 2016-02-18
Attempting to add Extension Manager app &#8220;LanguageToolstable.oxt to LibreOffice for grammar check and I get this error message:

```
(com.sun.star.uno.RuntimeException) { { Message = "[jni_uno bridge error] UNO calling Java method writeRegistryInfo: non-UNO exception occurred: java.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000ajava stack trace:\X000ajava.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000a\X0009at java.lang.ClassLoader.defineClass1(Native Method)\X000a\X0009at java.lang.ClassLoader.defineClass(ClassLoader.java:800)\X000a\X0009at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)\X000a\X0009at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)\X000a\X0009at java.net.URLClassLoader.access$100(URLClassLoader.java:71)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:361)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:355)\X000a\X0009at java.security.AccessController.doPrivileged(Native Method)\X000a\X0009at java.net.URLClassLoader.findClass(URLClassLoader.java:354)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:425)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:412)\X000a\X0009at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:793)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:358)\X000a\X0009at com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:52)\X000a\X0009at com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:380)\X000a", Context = (com.sun.star.uno.XInterface) @0 } }
```

Is the problem the choice of Java the reason for the error message?

```
Installed Icedtea Java Plugin, icedtea-plugin 1.5.3-OubuntuO.15.10.1 and I still get this message:
[jni_uno bridge error] UNO calling Java method writeRegistryInfo: non-UNO exception occurred: java.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0
java stack trace:
java.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:800)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:71)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:361)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:412)
    at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:793)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
    at com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:52)
    at com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:380)
```

---

### Post by Linuxisfast on 2016-02-19
[http://extensions.libreoffice.org/extension-center/languagetool](http://extensions.libreoffice.org/extension-center/languagetool) if you mean this one make sure you have libreoffice-java-common installed and it also needs jre-8 and if on Trusty you need ppa for it at [https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa](https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa)

---

### Post by TWFJR on 2016-02-19
Listing Java applications loaded on my computer,Ubuntu 15.10:

OpenJDK Java 8 Runtime
OpenJDK Java 7 Runtime
OpenJDK Java 6 Runtime
Icedtea Java Plugin
OpenJDK Java 8 Policy Tool
IcedTea Java Web Start

I do not see libreoffice-java-common listed on Ubuntu Software Center nor Synaptic.

I installed jre-8.

I still get the error message:

(com.sun.star.uno.RuntimeException) { { Message = "[jni_uno bridge error] UNO calling Java method writeRegistryInfo: non-UNO exception occurred: java.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000ajava stack trace:\X000ajava.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000a\X0009at java.lang.ClassLoader.defineClass1(Native Method)\X000a\X0009at java.lang.ClassLoader.defineClass(ClassLoader.java:800)\X000a\X0009at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)\X000a\X0009at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)\X000a\X0009at java.net.URLClassLoader.access$100(URLClassLoader.java:71)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:361)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:355)\X000a\X0009at java.security.AccessController.doPrivileged(Native Method)\X000a\X0009at java.net.URLClassLoader.findClass(URLClassLoader.java:354)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:425)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:412)\X000a\X0009at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:793)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:358)\X000a\X0009at com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:52)\X000a\X0009at com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:380)\X000a", Context = (com.sun.star.uno.XInterface) @0 } }

---

### Post by Linuxisfast on 2016-02-20
> **TWFJR said:**
> Listing Java applications loaded on my computer,Ubuntu 15.10:

OpenJDK Java 8 Runtime
OpenJDK Java 7 Runtime
OpenJDK Java 6 Runtime
Icedtea Java Plugin
OpenJDK Java 8 Policy Tool
IcedTea Java Web Start

I do not see libreoffice-java-common listed on Ubuntu Software Center nor Synaptic.

I installed jre-8.

I still get the error message:

(com.sun.star.uno.RuntimeException) { { Message = "[jni_uno bridge error] UNO calling Java method writeRegistryInfo: non-UNO exception occurred: java.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000ajava stack trace:\X000ajava.lang.UnsupportedClassVersionError: org/languagetool/openoffice/Main : Unsupported major.minor version 52.0\X000a\X0009at java.lang.ClassLoader.defineClass1(Native Method)\X000a\X0009at java.lang.ClassLoader.defineClass(ClassLoader.java:800)\X000a\X0009at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)\X000a\X0009at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)\X000a\X0009at java.net.URLClassLoader.access$100(URLClassLoader.java:71)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:361)\X000a\X0009at java.net.URLClassLoader$1.run(URLClassLoader.java:355)\X000a\X0009at java.security.AccessController.doPrivileged(Native Method)\X000a\X0009at java.net.URLClassLoader.findClass(URLClassLoader.java:354)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:425)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:412)\X000a\X0009at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:793)\X000a\X0009at java.lang.ClassLoader.loadClass(ClassLoader.java:358)\X000a\X0009at com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:52)\X000a\X0009at com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:380)\X000a", Context = (com.sun.star.uno.XInterface) @0 } }



[https://launchpad.net/ubuntu/wily/+package/libreoffice-java-common](https://launchpad.net/ubuntu/wily/+package/libreoffice-java-common)

---

### Post by TWFJR on 2016-02-20
Is the problem the choice of Java the reason for the error message?

Before I install “libreoffice-java-common,” what I have installed is:
Version: 5.0.5.2
Build ID: 1:5.0.5~rc2-0ubuntu2
Locale: en-US (en_US.UTF-8).

Explain what concerns I should have if I install “libreoffice-java-common with the above version already installed. I have many files with the above installed version of LibreOffice, are they going to be lost with a new installation?

Also, with multiple Java installations, is this a problem?
I am also confused with all the binary packages listed at [https://launchpad.net/ubuntu/+source/libreoffice/1:5.0.5~rc2-0ubuntu2](https://launchpad.net/ubuntu/+source/libreoffice/1:5.0.5~rc2-0ubuntu2) .
These are the options for download: 
Downloads
File
Size
MD5 Checksum
libreoffice_5.0.5~rc2.orig-src.tar.xz 
172.9 MiB
a31104d8b0bb1813694bc8a383c8ab05
libreoffice_5.0.5~rc2.orig-translations.tar.xz 
124.0 MiB
d6dea839619296d0db516e8b9c81923f
libreoffice_5.0.5~rc2.orig.tar.xz 
140.5 MiB
aced7c00c43be3bd687523d590a5cbd7
libreoffice_5.0.5~rc2-0ubuntu2.debian.tar.xz 
2.0 MiB
5b9be420c9c530cc3583984e6e62564b
libreoffice_5.0.5~rc2-0ubuntu2.dsc 
14.2 KiB
1c3bce03e09366be08d0a8256482723a

None of these indicates  “libreoffice-java-common.”

So, what I need is some assistance regarding what packages I should install. I need to know if I need to delete, remove packages already installed.

---


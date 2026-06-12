---
title: "Feisty PHP Eclipse crash"
date: 2007-05-01
forum: General Help
---

### Post by seppo on 2007-05-01
I was wondering if i am the only one having difficulties getting Eclipse with PHP eclipse working. I tried the repo and non-repo version of Eclipse, together with the CVS version of PHP Eclipse. When I'm trying to save a PHP file, Eclipse crashes with an exit code 1:

```
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb28f5a0b, pid=15954, tid=3084282768
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libxpcom_core.so+0x97a0b]  _ZN18nsAString_internal6AssignERKS_+0x1b
#
# An error report file with more information is saved as hs_err_pid15954.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp

```Java version:
```
ii  sun-java6-bin                              6-00-2ubuntu2                          Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-fonts                            6-00-2ubuntu2                          Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jre                              6-00-2ubuntu2                          Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                           6-00-2ubuntu2                          The Java(TM) Plug-in, Java SE 6

```I also tried using Sun Java 1.5, but the problem remains. This used to work on Edgy without any problems.

---

### Post by flossgeek on 2007-05-01
Hello, I am running the latest Sun Java 6 SDK with PHP Eclipse with no issues. I think we have differences due to the installations methods. 

I installed java with the following procedure:-

**Installing Java 6**

If you want the plugin for mozilla and the java runtime, then you would do the following in a terminal:-

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

If you want the jdk(for writing java and contains jre) do this:-

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

Once you have done either of these run:-

```
sudo update-java-alternatives -s java-6-sun
```

Finally open the jvm config file:-

```
gksudo gedit /etc/jvm
```

arrange lines in following order:-

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr

Save and exit.

I then downloaded Eclipse PHP version from the following link:-

[http://www.eclipse.org/downloads/download.php?file=/tools/pdt/downloads/drops/S20070401-RC3/all-in-one/pdt-all-in-one-S20070401_RC3-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/tools/pdt/downloads/drops/S20070401-RC3/all-in-one/pdt-all-in-one-S20070401_RC3-linux-gtk.tar.gz)

Extracted the eclipse tar package in my home directory and then ran the eclipse executable file. Everything is fine for myself.

---

### Post by seppo on 2007-05-01
thanks for your recommendations! Right now my laptop is at the office, so I'll give it a try tomorrow, but I don't see the major differences in installations methods.

I installed the Eclipse 3.2.2 SDK from eclipse.org  (only difference is  I used [eclipse-SDK-3.2.2-linux-gtk.tar.gz]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/download.php?dropFile=eclipse-SDK-3.2.2-linux-gtk.tar.gz") ) and installed sun-java6 the way you described.

Eclipse itself is running fine, but when I'm running the PHP Eclipse plugin (tried v 1.1.9, which should work in Eclipse 3.2), Eclipse dies upon saving files.

I'll post my findings tomorrow.

[EDIT]
I think we have a misunderstanding: with PHP Eclipse I mean this plugin

[http://sourceforge.net/project/showfiles.php?group_id=57621](http://sourceforge.net/project/showfiles.php?group_id=57621)

Not the build in PHP support (which is very limited)
[/EDIT]

---

### Post by flossgeek on 2007-05-01
So the setup is fine, it may be the plugin, 

I don't use the plugin but use the PDT (PHP Development Tools framework), an eclipse build for PHP out of the box.

[http://download.eclipse.org/tools/pdt/downloads/index.php](http://download.eclipse.org/tools/pdt/downloads/index.php)

---

### Post by seppo on 2007-05-01
I'll give PDT a try tomorrow. I tried it a couple of months ago, but it was still in an alpha stage so it didn't work as well as PHPeclipse.  How does it compare to PHPeclipse in the current stage?

---

### Post by flossgeek on 2007-05-02
Be honest Im impressed with it, and prefer it to the plugin, try it I think you will like it.

---

### Post by seppo on 2007-05-02
Thanks flossgeek! :KS

PDT is much approved since my last install. Goodbye PHPeclipse, welcome PDT :)

---

### Post by frosas on 2007-05-04
I had the same problem (crashing on libxpcom_core.so) and it was due to PHPeclipse browser. Disabling it solved the problem.

---

### Post by depi on 2007-06-25
> **frosas said:**
> I had the same problem (crashing on libxpcom_core.so) and it was due to PHPeclipse browser. Disabling it solved the problem.

Yeah it works, hope there will be any bug fix for this in the future.

---

### Post by lightstream on 2007-08-03
My PHP Eclipse was crashing with error code 1 as soon as I opened a PHP file so I tried disabling the PHP browser (Windows > Preferences > PHPeclipse Web Development > Browser Preview Default > uncheck both items). Interesting that the PHP Browser tab is still there at the bottom of the edit view, but clicking the 'Play' button there does crash Eclipse, at least on my system (goes into some infiinite loop, and the same error message pops up when I force quit the program)

I guess the PHP Browser is the bit that lets you step through PHP code for debugging? Shame it's not working then!

---

### Post by c0ntax on 2007-10-20
> **frosas said:**
> I had the same problem (crashing on libxpcom_core.so) and it was due to PHPeclipse browser. Disabling it solved the problem.

You sir, are a god send! Thanks for that. The fix works a treat (especially since I've never used the PHP Browser, so it wont be missed) ;-)

---

### Post by aot2002 on 2007-11-03
i use this in a bash script


#!/bin/bash
eclipse -vm /usr/bin/java -ws gtk

---

### Post by neilb on 2008-03-04
turning off php browser helped here too

---


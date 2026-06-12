---
title: "unable to install software through tar.gz2 archives"
date: 2013-12-22
forum: General Help
---

### Post by nashtrik on 2013-12-22
I have been trying to install a few softwares and games through tar.gz archives but get stuck due to errors while running the 'make' command and haven't been able to install a single software till today .I have tried to install gutenrint5.2.9, cups 1.7.0 and a game criticalmass but haven't been able to install them,all stuck at the error cropping at the 'make' command,which I a unbale to resolve. here is the message I got upon installing criticalmass game today. .....

Making all in tinyxml
make[2]: Entering directory `/home/drshrikant/criticalmass/CriticalMass-1.0.2/tinyxml'
g++ -DHAVE_CONFIG_H -I. -I. -I..     -W -Wall -fno-exceptions -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/X11R6/include -c -o tinyxmlparser.o tinyxmlparser.cpp
tinyxmlparser.cpp: In member function ‘virtual const char* TiXmlUnknown::Parse(const char*)’:
tinyxmlparser.cpp:319:35: error: ‘strchr’ was not declared in this scope
tinyxmlparser.cpp: In member function ‘virtual const char* TiXmlComment::Parse(const char*)’:
tinyxmlparser.cpp:343:37: error: ‘strstr’ was not declared in this scope
tinyxmlparser.cpp: In member function ‘const char* TiXmlAttribute::Parse(const char*)’:
tinyxmlparser.cpp:408:29: error: ‘strchr’ was not declared in this scope
tinyxmlparser.cpp:413:28: error: ‘strchr’ was not declared in this scope
tinyxmlparser.cpp: In member function ‘virtual const char* TiXmlDeclaration::Parse(const char*)’:
tinyxmlparser.cpp:477:41: error: ‘strstr’ was not declared in this scope
make[2]: *** [tinyxmlparser.o] Error 1
make[2]: Leaving directory `/home/drshrikant/criticalmass/CriticalMass-1.0.2/tinyxml'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/drshrikant/criticalmass/CriticalMass-1.0.2'
make: *** [all] Error 2
drshrikant@shrinehguntinks:~/criticalmass/CriticalMass-1.0.2$                


Any solutions to rectify this error...? Thanks....

---

### Post by philinux on 2013-12-22
Open a terminal. 

sudo apt-get install criticalmass

Cups is already installed.

---

### Post by nashtrik on 2013-12-22
Thanks for the reply...and suppose I want to upgrade Cups to a newer version, then....?Also, 'sudo apt-get install gutenprint' is unable to locate the package 'gutenprint'....any solutions...?

---

### Post by steeldriver on 2013-12-22
The idea of a 'distro' is that you *don't* want to upgrade particular packages to newer versions - since it's quite likely to break other installed software. Upgrading particular packages (especially from source tarballs) is really a last resort when there's a particular feature or fix that you absolutely can't do without

The gutenprint package you are looking for may be named something slightly different such as 'libgutenprint' or 'printer-driver-gutenprint' - you can check the matching packages with apt-cache e.g.

```

apt-cache search gutenprint

```

or search for it in the Software Center app (or other GUI package manager such as synaptic)

---


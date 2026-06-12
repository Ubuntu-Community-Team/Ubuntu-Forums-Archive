---
title: "Maple 11 installation problem"
date: 2008-05-25
forum: General Help
---

### Post by andreselsuave on 2008-05-25
Hello ! I had no problem to install maple 11 using FEDORA from it's .bin file : Maple11Linux32Installer.bin
But I can't install it on Ubuntu Hardy. I do the following:
```
chmod a+x ./Maple11Linux32Installer
./Maple11Linux32installer
```
and I get this output:
```
./Maple11Linux32Installer.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2481: /tmp/install.dir.10614/Linux/resource/jre/bin/java: not found

```
I think it has something to do with java, because maple installer uses java. I get this when I do java -version :
```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)
```
Thanks a lot for your help in advance !! :)

---


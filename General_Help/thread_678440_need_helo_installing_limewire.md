---
title: "need helo installing limewire"
date: 2008-01-25
forum: General Help
---

### Post by 565Customz on 2008-01-25
ive got the disk here but how do i put it on my  /shared drive (ntfs) so that windows can access it as well..(dual boot)

---

### Post by LukeCarrier on 2008-01-26
Hello there,

I don't understand what you're asking, but if you want to install LimeWire on your Ubuntu-based PC, you might want to check out FrostWire ([http://www.frostwire.com/](http://www.frostwire.com/)), as they do a nice Ubuntu installer. FrostWire is built on LimeWire, and looks almost identical. You can still download files from LimeWire peers with it too.

Hope this helps,
Luke.

---

### Post by 565Customz on 2008-01-26
helps very much thanks

---

### Post by einherier on 2008-01-28
I dont know if i am supposed to start a new thread or not.  So ill just dump it here.  I keep trying to install frostwire and it says it installs and it goes in under applications>>Internet

but when i click the button....nothing happens :(

---

### Post by einherier on 2008-01-28
i try to remove it so i can try it again, but i cant find it under the add/remove programs even after selecting "show installed"

---

### Post by me4oslav on 2008-01-28
Have you tried executing it from terminal:
```
chichovoto6@tototo:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```
If you get the same thing try installing the [following file]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=12791").
```
**cd /path/to/file/**
```
```
**sh ./jre-6u3-linux-i586.bin**
```
This should upgrade your java to proper version for running FrostWire.Good Luck.

---

### Post by einherier on 2008-01-28
I need to learn more about the terminal...  I tried typing what you told me, but i think that maybe when you indicated path/to/data, you meant for me to actually go to the folder or whatever.  But i dont know much about using the linux command prompt......

---

### Post by wolfen69 on 2008-01-28
> But i dont know much about using the linux command prompt......
look at this [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by einherier on 2008-01-28
> **wolfen69 said:**
> look at this [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

cool, man, thanks....thats exactly what i've been needing

---


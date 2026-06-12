---
title: "Openoffice crash at startup"
date: 2019-02-27
forum: General Help
---

### Post by xonestarx86 on 2019-02-27
I recently reinstalled Ubuntu for the first time since I'd say about 2012.  I used to play with it a lot back in college, but really don't know how to do much anymore.  I am having trouble with running Open Office.  

When I try and open open office via the terminal, here is what it spits out. 

```
 soffice -writer
javaldx: Could not find a Java Runtime Environment!

```

So I installed Java, but I still seem to suffer from this issue. 
```
java -version
openjdk version "11.0.1" 2018-10-16
OpenJDK Runtime Environment (build 11.0.1+13-Ubuntu-3ubuntu3.18.10.1)
OpenJDK 64-Bit Server VM (build 11.0.1+13-Ubuntu-3ubuntu3.18.10.1, mixed mode, sharing)

```

Can anyone here help me fix this, or point me in the right direction of a more n00b friendly fix?  Thanks in advance.

---

### Post by Impavidus on 2019-02-28
The application used these days is libreoffice, although the command **soffice** works too as that's a symlink to the same application. And the proper way to state a long option is with two dashes, one-letter options use one dash. But it should recognise the option with a single dash as well, just give a warning message. You don't need java for libreoffice, you only need it for some optional functions.

So if you run```
libreoffice --write
```it should write some messages in the terminal and open a window for the program. It works here, without java:```
javaldx: Could not find a Java Runtime Environment!
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
```
What happens? Do you get your prompt back? Does it give some error? Do you not get a new prompt, but no libreoffice either (meaning libreoffice starts, but doesn't open a window)?

---

### Post by jsvidyad on 2019-02-28
You can run the command:
lowriter
This should open libreoffice writer

---

### Post by xonestarx86 on 2019-02-28
I'll just use Libreoffice.  That seems much easier at this point.  As long as I run these commands, this should clean everything out right?

sudo apt-get purge openoffice
sudo apt-get remove openoffice-debian-menus
sudo apt-get autoremove

---

### Post by Impavidus on 2019-02-28
Probably. You can use synaptic and search for remaining openoffice stuff.

Libreoffice is the one typically used on Ubuntu. Libreoffice and Openoffice cannot be installed at the same time. It seems that Libreoffice is the one with more active development.

---


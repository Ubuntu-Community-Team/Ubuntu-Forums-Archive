---
title: "Dell DJ drivers"
date: 2005-04-26
forum: General Help
---

### Post by spacemonkey on 2005-04-26
I want to be able to sync my dell dj in linux, but am having trouble getting the drivers installed.  Ubuntu's repositories has libnjb0, which is an older version of the driver I need.....I need libnjb4.  So I downloaded the source and compiled it.  Now if I try to install gnomad2 or neutrino from the repositories, it still wants to install libnjb0.  I tried compiling from source, which always gives me problems, and neutrino said this during ./configure : 

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Not sure what that means.  Debians unstable repository has the version ob libnjb that I need.  I've for [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable, unstable, and testing all enabled in my sources, yet I still can't seem to install the new version from synaptic.  I'd be satisfied if I could compile from source, which the lib did just fine, but I can't get any program to use the lib to compile, and when I try to install one from synaptic, it installs and I assume uses the old lib along with it.

Any help would be greatly appreciated.

---

### Post by poofyhairguy on 2005-04-27
[QUOTE=spacemonkey]

Not sure what that means.  Debians unstable repository has the version ob libnjb that I need.  I've for [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable, unstable, and testing all enabled in my sources, yet I still can't seem to install the new version from synaptic.  I'd be satisfied if I could compile from source, which the lib did just fine, but I can't get any program to use the lib to compile, and when I try to install one from synaptic, it installs and I assume uses the old lib along with it.

Any help would be greatly appreciated.[/QUOTE]

YOu can install it from Sid. Just make sure its the only thing in your sources.list that isn't commented out. It needs to be by itself.

---

### Post by spacemonkey on 2005-04-28
Sid??  Sorry, I'm a bit new to the apt thing.

---

### Post by bennettg on 2005-04-30
I am having the same problem.  I made some progress by looking at:

[http://www.mialug.org/index.php?option=com_simpleboard&Itemid=40&func=view&id=1264&catid=112](http://www.mialug.org/index.php?option=com_simpleboard&Itemid=40&func=view&id=1264&catid=112)

I used synaptic to download gnomad and the libnjb drivers.  However, when I start gnomad, at try to connect to my dell dj, I get the following error:

"Could not open jukebox"

Does anyone know what this means. Is ubuntu not seeing the dell dj device?  i dont know what command to enter to determine this.

 I am a nOOb, but love Ubuntu and this is the last step I need to accompliash before ditching M$.

---

### Post by bennettg on 2005-04-30
Went to [www.ubuntuguide.org](www.ubuntuguide.org) and found out how to list mounted usb devices:

bennettg@ubuntu:~$ lsusb
Bus 004 Device 002: ID 041e:4111 Creative Technology, Ltd Dell Digital Jukebox
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
bennettg@ubuntu:~$


Does anyone know what the problem with gnomad is?  ubuntu sees my dell dj player, but gnomad can't open it.

---

### Post by spacemonkey on 2005-04-30
My dj also show up in lsusb.  We're in the same boat bennettg.

---

### Post by bennettg on 2005-04-30
yes, but can anyone help us?

---

### Post by blakdogg on 2005-06-05
Try starting gnomad2 as root - 'sudo gnomad2'. Mine works with the 'included' gnomad2 when I run it as root. There is a thread that seems to deal with this.

[http://ubuntuforums.org/showthread.php?t=34018&highlight=dell+dj](http://ubuntuforums.org/showthread.php?t=34018&highlight=dell+dj)

---


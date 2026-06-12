---
title: "Trouble installing Java"
date: 2005-04-28
forum: General Help
---

### Post by cutOff on 2005-04-28
Hi there

when i try to update from 

> deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/
deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 

i get this error

> Err [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) binary/ Packages
  Imposible traer archivo, el servidor dijo 'Failed to open file.  '
Des:16 [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) source/ Sources
Err [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) source/ Sources
  Imposible traer archivo, el servidor dijo 'Failed to open file.  '
Descargados 150kB en 10s (14,2kB/s)
Imposible obtener [ftp://neacm.fe.up.pt/pub/ubuntu-java/binary/Packages.gz](ftp://neacm.fe.up.pt/pub/ubuntu-java/binary/Packages.gz)  Impos ible traer archivo, el servidor dijo 'Failed to open file.  '
Imposible obtener [ftp://neacm.fe.up.pt/pub/ubuntu-java/source/Sources.gz](ftp://neacm.fe.up.pt/pub/ubuntu-java/source/Sources.gz)  Imposi ble traer archivo, el servidor dijo 'Failed to open file.  ' 
Anyone else is having same problem??

Regards

---

### Post by tread on 2005-04-28
Maybe server's down? I dunno how to solve your problem, but if you just want java working quickly you can go to suns website and download java for linux there .. pretty simple instructions and they work. (did for me at least! :))

---

### Post by cutOff on 2005-04-28
Thanx for the suggestion.

I'll do it.


Regards

---

### Post by mostwanted on 2005-04-28
I have a .deb of jdk 5_0_2 lying around somewhere. It works by just installing with dpkg.

---

### Post by bored2k on 2005-04-28
[QUOTE=cutOff]Thanx for the suggestion.

I'll do it.


Regards[/QUOTE]
 [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) after adding their repositories sudo apt-get install sun-j2re1.5

---

### Post by DutchLau on 2005-04-28
Might this: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)  Help you?

Let us know if you had any success,

DutchLau

---

### Post by cutOff on 2005-04-28
Thanx to all. 

It's already solved.

I followed the steps of the guide. 



Regards!

---

### Post by cutOff on 2005-04-29
[QUOTE=bored2k][http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) after adding their repositories sudo apt-get install sun-j2re1.5[/QUOTE]
Question: does this package install java-plugin for Firefox and create the appropiate symlink ??

---

### Post by cutOff on 2005-04-30
Does anybody know about this?? Please.

---

### Post by bored2k on 2005-04-30
[QUOTE=cutOff]Question: does this package install java-plugin for Firefox and create the appropiate symlink ??[/QUOTE]
 Yes it does.

---

### Post by cutOff on 2005-04-30
Ok thanx a lot.

---


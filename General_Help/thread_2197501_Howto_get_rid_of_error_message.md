---
title: "Howto get rid of error message"
date: 2014-01-04
forum: General Help
---

### Post by claracc on 2014-01-04
When is used the command dpkg (through apt-install or other commands which invokes dpkg) I obtain the following error message since I upgraded to ubuntu 12.04 ( long time ago), i.e.:

```
dpkg --get-selections | grep linux-image
dpkg: aviso: analizando archivo «/var/lib/dpkg/status» cerca de la línea 39264 paquete «mac-3.99-u4»:
 error en la cadena `Version' `b3-1': el número de versión no empieza por un dígito

```

Translation:

```
dpkg --get-selections | grep linux-image
dpkg: Notice: analyzing file «/var/lib/dpkg/status» near line 39264 package «mac-3.99-u4»:
 error in the chain `Version' `b3-1': The number of version doesn't start by a digit

```

I would like to get rid of this error message, could someone indicates the  way, please?

Thanks in advance

---

### Post by bapoumba on 2014-01-04
May be here ?
[http://ubuntuforums.org/showthread.php?t=1394319](http://ubuntuforums.org/showthread.php?t=1394319)
[http://ubuntuforums.org/showthread.php?t=1776671](http://ubuntuforums.org/showthread.php?t=1776671) post #6
[http://ubuntuforums.org/showthread.php?t=1816855](http://ubuntuforums.org/showthread.php?t=1816855)

---

### Post by claracc on 2014-01-06
Thank you very much.

Follwing the thread provided [http://ubuntuforums.org/showthread.php?t=1776671](http://ubuntuforums.org/showthread.php?t=1776671) I have solved the problem in the following way:

As the files in /var/lib/dpkg/status and /var/lib/dpkg/status-old seem to be corrupted, directly I have deleted all the information about the culprit software package, mac-3.99-u4,  in the satus file, then I have used the two commands provided in the forementioned thread:

```
sudo dpkg --clear-avail
sudo apt-get update
```

And evverything is okay now, the error message has disappeared when I run i.e.:  

```
 dpkg --get-selections | grep linux-image

```

I obtain:

```
linux-image-3.2.0-57-generic			install
linux-image-3.2.0-58-generic			install
linux-image-generic				install
clara@clara1:/var/lib/dpkg$ 

```

---

### Post by bapoumba on 2014-01-06
:happy_for_you:

---


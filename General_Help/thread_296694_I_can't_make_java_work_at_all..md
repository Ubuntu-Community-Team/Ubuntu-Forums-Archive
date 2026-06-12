---
title: "I can't make java work at all."
date: 2006-11-10
forum: General Help
---

### Post by WetWired on 2006-11-10
I can't seem to make java work no matter what I try. I've tried automatix2, and it can't even do it. I'm wanting to be able to use java in my browser (firefox) and I'm also wanting to run FrostWire. Here's the output when I try to run FrostWire, maybe one of yall can tell me what to do.


```
robbie@ubuntu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
robbie@ubuntu:~$

```




```
robbie@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
robbie@ubuntu:~$

```

---

### Post by jpkotta on 2006-11-10
Try Sun's Java.  I've had the best luck with that.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by IusedTObeSOMEONEelse on 2006-11-10
I am no expert but if your on dapper, in Applications>Add/Remove  I ticked off java 1.4 but I remember I had to checkthe boxes 'supported" & 'non-supported' (or comercial) you'll see the 2 little boxes on Add/Remove. hope it helps!! :p  :-k

---

### Post by WetWired on 2006-11-10
I'm still not getting it. I'm not sure what to do.

---

### Post by taurus on 2006-11-10
Use autoamtix2 and install java on your machine!!!

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by WetWired on 2006-11-10
Automatix2 doesn't work. I've tried it. Something about not being able to find an alternative or something.

---

### Post by taurus on 2006-11-10
> **WetWired said:**
> Automatix2 doesn't work. I've tried it. Something about not being able to find an alternative or something.
How did you install automatix2 anyway?

---

### Post by WetWired on 2006-11-11
May not be automatix2, it may just be automatix. Either way, it wouldn't install java.

---

### Post by zadax on 2006-11-11
install the latest "sun java" from the synaptic package manager (see above link for more info).  then run  "update-alternatives --config java" and select sun's java.

if you just want to do it by hand from java.sun.com's dowload, then see here:   [http://www.ubuntuforums.org/showthread.php?t=297770](http://www.ubuntuforums.org/showthread.php?t=297770)

---

### Post by WetWired on 2006-11-12
> install the latest "sun java" from the synaptic package manager (see above link for more info). then run "update-alternatives --config java" and select sun's java.

That worked. Thanks.

---

### Post by IamAcoconut on 2006-12-27
It worked for me as well, while all the other ways failed. It took me a long time to find this thread though - why don't stick it?

---


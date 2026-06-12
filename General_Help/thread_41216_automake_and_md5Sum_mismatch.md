---
title: "automake and md5Sum mismatch"
date: 2005-06-12
forum: General Help
---

### Post by pietro_spina on 2005-06-12
Hey y'all,

I get this error when I attempt to install automake1.4 and indent using synaptic...

> Warning:
The following problems were found on your system:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake/automake1.4_1.4-p6-8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake/automake1.4_1.4-p6-8_all.deb)
  MD5Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/indent/indent_2.2.9-6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/indent/indent_2.2.9-6_i386.deb)
  MD5Sum mismatch

<--a little CLI justy for fun-->
$ sudo apt-get clean
$ sudo apt-get update

<--tried the following (both failed with same error)-->
$ sudo apt-get install automake1.4
$ sudo apt-get --fix-missing install automake1.4

Do you have any thoughts how to fix this?

thanks,
P

---

### Post by Njall on 2005-06-12
heh heh... I JUST had this exact problem.  I resolved it by going to the URL listed and picking the latest automake DEB file and downloading it.  Then 

$ sudo dpkg --install automake1.4_1.4-p6-9_all.deb

Then in synaptic I believe you will see that autoconf is A-OK.

---

### Post by pietro_spina on 2005-06-12
Also, see this thread for what seems to be a similar problem...

[http://www.ubuntuforums.org/showthread.php?t=40895](http://www.ubuntuforums.org/showthread.php?t=40895)

If it is truly a flaky mirror... 

Well I'm not totally impatient... I'll try again tomorrow...

cheers,
-p

---

### Post by ubuntu_demon on 2005-06-14
Hi, guys. let's continue all md5 threads here :

[http://www.ubuntuforums.org/showthread.php?t=41647](http://www.ubuntuforums.org/showthread.php?t=41647)

I'm closing this thread

---


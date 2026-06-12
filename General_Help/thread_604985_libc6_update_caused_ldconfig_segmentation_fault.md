---
title: "libc6 update caused ldconfig segmentation fault"
date: 2007-11-06
forum: General Help
---

### Post by PhP67 on 2007-11-06
Hi

My current Ubuntu version is Gutsy. The update manager caused me to upgrade the libc6 package today. When completing the libc6 configuration, it displayed the error message as shown below. I also get the same if I run "dpkg --configure -a"

[COLOR="Blue"][FONT="Courier New"]Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/var/lib/dpkg/info/libc6.postinst: line 15:  6904 Segmentation fault (core dumped) ldconfig
dpkg: subprocess post-installation script returned error exit status 139[/FONT][/COLOR]

Any idea how I can solve this?

Thanks
Philippe

---

### Post by nostix on 2007-11-08
Hi,

I've the same problem after installing some new packages today.
I always get the error message:

Richte libc6 ein (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault (core dumped)
dpkg: Unterprozess post-installation script gab den Fehlerwert 139 zurück
E: Sub-process /usr/bin/dpkg returned an error code (2)

After executing the following commands I still get the same error:
dpkg --configure -a
apt-get update
apt-get upgrade

---

### Post by pkese on 2007-11-08
Same here:

[COLOR="Navy"][I]peter@carbon:~$ sudo dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault (core dumped)
dpkg: subprocess post-installation script returned error exit status 139[/I][/COLOR]

---

### Post by nostix on 2007-11-09
I got it by manually downloading the package from

[http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)

then I just installed the package with

dpkg -i libc6_2.6.1-1ubuntu10_i386.deb

\\:D/

---

### Post by PhP67 on 2007-11-09
Well... thanks for the hint.... but something must have gone wrong! I downloaded the package and started the install. Then it used 100% CPU for a while (I have a dual core) and 100% memory (2 GB), and did not move any more. I could not start anything else in parallel (could not fork).

I stopped the PC and rebooted: it did not boot any more...

Fortunately I had a recent backup so I could restore my / and /usr, which restored everything.... 

Don't know what went wrong, if it's inside the package or specific to my setup.

PS: guess what? while I was typing this response on my restored system, Gnome asked me if I wanted to download the same package again :confused:

---

### Post by PhP67 on 2007-11-09
Ok, after my previous message, I stopped gdm, went to a text terminal, and executed "apt-get install libc6" manually in order to perform the update. I had prepared a backup of /sbin/ldconfig.real, just in case.
This time the update went ok. Didn't need my backuped ldconfig.real... no idea why it worked this time and not the other day.:(

---

### Post by malan_in on 2008-02-24
Hi guys,
i also tried to manual install the package. Still i have the same error. Any updated information?

---


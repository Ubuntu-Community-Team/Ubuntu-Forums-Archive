---
title: "`GCC_4.2.0' not found (required by /usr/lib/libstdc+"
date: 2006-10-03
forum: General Help
---

### Post by hanzomon4 on 2006-10-03
I get this when trying to run certain apps like glxinfo, IE for linux, and vmware-server. The first two won't start and I had problem with firefox spitting out the same thing and not starting, luckily after a reboot firefox stopped complaining.

Here is the complete error message ```
 /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

I'm lost as there is no gcc-4.2.0 in the repos. Any help would be appreciated [-o<

---

### Post by xXx 0wn3d xXx on 2006-10-03
> **hanzomon4 said:**
> I get this when trying to run certain apps like glxinfo, IE for linux, and vmware-server. The first two won't start and I had problem with firefox spitting out the same thing and not starting, luckily after a reboot firefox stopped complaining.

Here is the complete error message ```
 /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

I'm lost as there is no gcc-4.2.0 in the repos. Any help would be appreciated [-o<

Do you have build and gcc installed ? Try:

> sudo apt-get install build-essential

---

### Post by hanzomon4 on 2006-10-03
Yes I have gcc v3.4, gcc v4.0, and gcc v4.1. I did the apt-get build-essential and it didn't install anything.

---

### Post by hanzomon4 on 2006-10-03
I found something, its a bug with libstdc++6 v4.1.1-13. [Link to bug report]("http://www.mail-archive.com/debian-gcc@lists.debian.org/msg21557.html"). 

When I run this command ```
strings /usr/lib/libstdc++.so.6 | grep ^GCC
``` I get this output 
```
 strings /usr/lib/libstdc++.so.6 | grep ^GCC
GCC_3.3
GCC_4.2.0
GCC_3.0

```

Anybody no a work around, like how to downgrade the package.

---

### Post by hanzomon4 on 2006-10-05
Crap! I'm starting to get this error for other apps
```
openoffice
/usr/lib/openoffice/program/javaldx: /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/openoffice/program/pagein: /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/openoffice/program/soffice.bin: /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

** (process:32135): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

---

### Post by hanzomon4 on 2006-10-07
The problem goes away if I run the offending apps as root... Don't know why?

---

### Post by David Corrales on 2006-10-07
What are the permissions for those libraries?

---

### Post by hanzomon4 on 2006-10-08
```
-rw-r--r-- 1 root root 220855 2006-10-01 12:45 /usr/lib/libgcc_s.so.1
```
This next one is a symlink 
```
lrwxrwxrwx 1 root root 18 2006-10-03 19:59 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.8

```
This is the target
```
-rw-r--r-- 1 root root 888612 2006-09-30 09:39 /usr/lib/libstdc++.so.6.0.8
```

---

### Post by hanzomon4 on 2006-10-11
I fixed it.....   Following a tip, I ldd /usr/lib/libstdc++.so.6...
```

ldd /usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6: /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ede000)
        [COLOR="Red"]**libgcc_s.so.1 => /usr/lib/libgcc_s.so.1 (0xb7ed3000)**[/COLOR]
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d9e000)
        /lib/ld-linux.so.2 (0x80000000)

```  

I then mv the libgcc_s.so.1 
```
 sudo mv /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1.old
```

This fixed the error and the apps started to act right, the problem with openoffice is different and I haven't fixed that yet.. 
```
ooffice -writer
pure virtual method called
terminate called without an active exception
/usr/lib/openoffice/program/soffice: line 254: 31037 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:31021): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

---

### Post by David Corrales on 2006-10-12
Have you tried using the packages from OpenOffice.org? I installed them over the Ubuntu ones (using alien to convert rpm's) and they work faster and more reliably. The only missing piece is startup notification.

---

### Post by hanzomon4 on 2006-10-12
No, but I get working again.. not sure how though.

---

### Post by phizzzt on 2007-08-02
Just so everyone knows,

I was able to fix this error by changing a symbolic link in /usr/lib to point to /lib instead of /usr/local/lib, like this:

libgcc_s.so.1 -> /usr/local/lib/libgcc_s.so.1

was changed to point to /lib using this command as root (after backing up a copy of the libgcc_s.so.1, of course):

ln -s /lib/libgcc_s.so.1 libgcc_s.so.1

while still in the /usr/lib dir. The reason for this on my machine is that I upgraded libstdc++ to a newer version using apt-get and then my "ldconfig" ured path was finding /usr/lib before /lib where the newer version of libgcc_s.so.1 is: 

libgcc_s-4.1.1-20070108.so.1


Thanks,
phizzzt

---

### Post by doug84065 on 2007-08-18
Yes, thanks a lot!  That probably took a lot of time to track down.  Now openoffice will open again.

 cd /usr/lib
 sudo ln -s /lib/libgcc_s.so.1 libgcc_s.so.1

---

### Post by Dambrosio on 2008-05-30
I have tried to follow your instructions to move libgcc_s.so.1 to libgcc_s.so.1.old but this is what i get:

```
ambrosio@ambrosio-laptop:/usr/lib$ ldd /usr/lib/libstdc++.so.6
	linux-gate.so.1 =>  (0xb7f8c000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e61000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e56000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d06000)
	/lib/ld-linux.so.2 (0xb7f8d000)

```

```
ambrosio@ambrosio-laptop:/usr/lib$ sudo mv /usr/lib/libcc_s.so.1 /usr/lib/libgcc_s.so.1.old
mv: cannot stat `/usr/lib/libcc_s.so.1': No such file or directory

```

I don't understand why it cant find the file, what am I doing wrong?

Thanks,
Dan

---

### Post by Xavieran on 2008-06-13
I think I am also having the same problem as Dan, the two computers that I upgraded to ubuntu 8.04 say that they need GCC_4.2.0 (required by libstdc++.so.6.
Do you think it would be safe to uninstall libstdc++6
I also have libstdc++6-4.2-dev installed, is it necessary?
Thanks,
Xavieran

---

### Post by fowie on 2008-07-20
Turns out my problem stemmed from a bad version of /usr/lib/libstdc++.so.6, it was linking to /usr/lib/libstdc++.so.6.8 (which apparently wasn't working right on my system).  Try this:

```

sudo mv /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.6.oldlink
sudo ln -s /usr/lib/libstdc++.so.6.0.7 /usr/lib/libstdc++.so.6

```

---


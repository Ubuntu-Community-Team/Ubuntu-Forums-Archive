---
title: "Problems with installing Sun Java EE SDK"
date: 2008-04-26
forum: General Help
---

### Post by olegol on 2008-04-26
I've downloaded the file: java_ee_sdk-5_04.bin from java.sun.com and then I did the following:

1. chmod +x *.bin
2. ./java_ee_sdk-5_04.bin

After the command in point 2 above executes I get the following error message:
bash: ./java_ee_sdk-5_04.bin: No such file or directory

Please note that my current directory/present working directory contains the file and this bin runs in Debian 4.0r3 and in openSuse 10.3, but doesn't in ubuntu (and kubuntu) 8.04. I've tried sudo, to rename/move file, to change bash... nothing :(. The only idea I have that there is no some libs in my system...

---

### Post by ipatec on 2008-04-26
For me just worked perfect...

---

### Post by olegol on 2008-04-26
> **ipatec said:**
> For me just worked perfect...

Did you install it to the "blanc" system? I've tried to run bin on my friend's PC with ubuntu 8.04 & 7.10 and have this error too.

---

### Post by asfaraslarry on 2008-04-26
I'm having this same problem, and came here looking for a solution.

Not an answer, but you are not alone.

---

### Post by asfaraslarry on 2008-04-26
Is it possible this is our problem?

[http://ubuntuforums.org/archive/index.php/t-542315.html](http://ubuntuforums.org/archive/index.php/t-542315.html)

Are you running the AMD 64 Ubuntu as I am?

---

### Post by olegol on 2008-04-26
> **asfaraslarry said:**
> Is it possible this is our problem?

[http://ubuntuforums.org/archive/index.php/t-542315.html](http://ubuntuforums.org/archive/index.php/t-542315.html)

Are you running the AMD 64 Ubuntu as I am?

Yes! Ubuntu amd64 on Dell inspiron 1520. So the solution is to install ia32-libs compatibility libraries for 32 bit binaries?

---

### Post by asfaraslarry on 2008-04-27
I went ahead and performed the install from the link and ran 'getlibs' on the .bin file I was trying to install from Sun for the JDK and it downloaded and installed all the 32 bit libraries I seemed to need to get it going and then went back and ran the .bin afterwards and it worked like a champ.

Hopefully that works for you as well :)

---

### Post by unreger on 2008-09-23
8.04
Genue Intel Processor (is not AMD64 bug ... ia32 an so other...)
java_ee_sdk-5_05-linux.bin in my home folder, free space 90Gb

$./java_ee_sdk-5_05-linux.bin
Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...

and stoped

ok, kill it
another way

$ fakeroot make-jpkg ./java_ee_sdk-5_05-linux.bin 
Creating temporary directory: /tmp/make-jpkg.KgGPJ10656
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done

BUT
install SE JDK
$./jdk-6u7-linux-i586.bin
correctly worked

Ubuntu 8.04 can't work with Java EE? :confused:

---

### Post by unreger on 2008-09-23
$ sudo ./java_ee_sdk-5_05-linux.bin 
[sudo] password for smith: 
Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...
*** glibc detected *** ./java_ee_sdk-5_05-linux.bin: double free or corruption (!prev): 0x08072d70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7ceba85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cef4f0]
./java_ee_sdk-5_05-linux.bin(GetPublicJREPath+0x6df)[0x8054269]
./java_ee_sdk-5_05-linux.bin(main+0x8f8)[0x804e37c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c96450]
./java_ee_sdk-5_05-linux.bin(dlopen+0x41)[0x804c9f5]
======= Memory map: ========
08048000-08061000 r-xp 00000000 08:06 4186207    /home/smith/distrib/java/java_ee_sdk-5_05-linux.bin
08061000-08063000 rw-p 00018000 08:06 4186207    /home/smith/distrib/java/java_ee_sdk-5_05-linux.bin
08063000-08095000 rw-p 08063000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0 
b7a21000-b7b00000 ---p b7a21000 00:00 0 
b7b5c000-b7b5d000 rw-p b7b5c000 00:00 0 
b7b5d000-b7b9c000 r--p 00000000 08:02 586243     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7b9c000-b7b9d000 r--p 00000000 08:02 586248     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7b9d000-b7c7e000 r--p 00000000 08:02 586242     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7c7e000-b7c80000 rw-p b7c7e000 00:00 0 
b7c80000-b7dc9000 r-xp 00000000 08:02 188282     /lib/tls/i686/cmov/libc-2.7.so
b7dc9000-b7dca000 r--p 00149000 08:02 188282     /lib/tls/i686/cmov/libc-2.7.so
b7dca000-b7dcc000 rw-p 0014a000 08:02 188282     /lib/tls/i686/cmov/libc-2.7.so
b7dcc000-b7dcf000 rw-p b7dcc000 00:00 0 
b7dcf000-b7dd9000 r-xp 00000000 08:02 170752     /lib/libgcc_s.so.1
b7dd9000-b7dda000 rw-p 0000a000 08:02 170752     /lib/libgcc_s.so.1
b7dda000-b7dfd000 r-xp 00000000 08:02 188290     /lib/tls/i686/cmov/libm-2.7.so
b7dfd000-b7dff000 rw-p 00023000 08:02 188290     /lib/tls/i686/cmov/libm-2.7.so
b7dff000-b7eaf000 r-xp 00000000 08:02 561337     /usr/lib/libstdc++.so.5.0.7
b7eaf000-b7eb4000 rw-p 000af000 08:02 561337     /usr/lib/libstdc++.so.5.0.7
b7eb4000-b7eb9000 rw-p b7eb4000 00:00 0 
b7eb9000-b7ec8000 r-xp 00000000 08:02 188310     /lib/tls/i686/cmov/libresolv-2.7.so
b7ec8000-b7eca000 rw-p 0000f000 08:02 188310     /lib/tls/i686/cmov/libresolv-2.7.so
b7eca000-b7ecc000 rw-p b7eca000 00:00 0 
b7ecc000-b7ed5000 r-xp 00000000 08:02 188286     /lib/tls/i686/cmov/libcrypt-2.7.so
b7ed5000-b7ed7000 rw-p 00008000 08:02 188286     /lib/tls/i686/cmov/libcrypt-2.7.so
b7ed7000-b7eff000 rw-p b7ed7000 00:00 0 
b7eff000-b7f01000 r-xp 00000000 08:02 188288     /lib/tls/i686/cmov/libdl-2.7.so
b7f01000-b7f03000 rw-p 00001000 08:02 188288     /lib/tls/i686/cmov/libdl-2.7.so
b7f03000-b7f17000 r-xp 00000000 08:02 188308     /lib/tls/i686/cmov/libpthread-2.7.so
b7f17000-b7f19000 rw-p 00013000 08:02 188308     /lib/tls/i686/cmov/libpthread-2.7.so
b7f19000-b7f1b000 rw-p b7f19000 00:00 0 
b7f1b000-b7f1c000 r--p 00000000 08:02 585488     /usr/lib/locale/en_US.utf8/LC_TIME
b7f1c000-b7f1d000 r--p 00000000 08:02 585489     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f1d000-b7f1e000 r--p 00000000 08:02 586168     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f1e000-b7f1f000 r--p 00000000 08:02 586227     /usr/lib/locale/en_US.utf8/LC_PAPER
b7f1f000-b7f20000 r--p 00000000 08:02 586225     /usr/lib/locale/en_US.utf8/LC_NAME
b7f20000-b7f21000 r--p 00000000 08:02 585490     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f21000-b7f22000 r--p 00000000 08:02 585491     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f22000-b7f23000 r--p 00000000 08:02 585492     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f23000-b7f2a000 r--s 00000000 08:02 114034     /usr/lib/gconv/gconv-modules.cache
b7f2a000-b7f2b000 r--p 00000000 08:02 585493     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f2b000-b7f2d000 rw-p b7f2b000 00:00 0 
b7f2d000-b7f2e000 r-xp b7f2d000 00:00 0          [vdso]
b7f2e000-b7f48000 r-xp 00000000 08:02 170707     /lib/ld-2.7.so
b7f48000-b7f4a000 rw-p 00019000 08:02 170707     /lib/ld-2.7.so
bfa08000-bfa1d000 rw-p bffeb000 00:00 0          [stack]
Deleting temporary files...

---


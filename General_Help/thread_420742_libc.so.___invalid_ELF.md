---
title: "libc.so.*  : invalid ELF???"
date: 2007-04-23
forum: General Help
---

### Post by atararx on 2007-04-23
Hi,
I recently upgraded my kubuntu system from 6.10 to 7.04.

I was using mzscheme (for school work) and it worked fine.
Unfortunately, right after the upgrade, if I type mzscheme, it gives me

$ mzscheme
mzscheme: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header

I have checked the links and they all exist.
$ ls -l /usr/lib/libc.*
-rw-r--r-- 1 root root 2825370 2007-04-04 06:48 /usr/lib/libc.a
-rw-r--r-- 1 root root     238 2007-04-04 06:31 /usr/lib/libc.so
lrwxrwxrwx 1 root root       7 2007-04-23 19:41 /usr/lib/libc.so.6 -> libc.so

$ dpkg -S /usr/lib/libc.so
libc6-dev: /usr/lib/libc.so

I  searched on-line but I could not find anything that could help me.
I get the same error when I try to install maple

$ ./Linux10Installer.bin.sh
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
dirname: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
basename: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
hostname: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header

Launching installer...

grep: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/tmp/install.dir.28883/Linux/resource/jre/bin/java: error while loading shared libraries: /usr/lib/libpthread.so.0: invalid ELF header


I tried "aptitude reinstall libc6" and it did not appear to help
(oh, before that I tried apt-get reinstall. When that failed, I tried apt-get 
remove libc6. That was pretty hilarious 

After unpacking 2505MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

And oh yeah, I did not type "Yes, do as I say!" even though I was tempted to :)

)

Thanks in advance for anything that can help me fix this problem(s).

---

### Post by atararx on 2007-04-24
I found the answer while searching through the web.
[http://openfoam.cfd-online.com/forum/messages/1/3777.html?1170687616](http://openfoam.cfd-online.com/forum/messages/1/3777.html?1170687616)

-----------------------------------


Hi
I came across the following message when I ve installed OpenFOAM on gentoo.

icoFoam: error while loading shared libraries: /usr/lib/libz.so: invalid ELF header

the problem is with the place where the libraries are in gentoo. In short gentoo puts:

shared lib in /lib
static archive in /usr/lib
libtool script in /usr/lib
linker script in /usr/lib that points to /lib

FIX for it is simple:

cd /usr/lib
ln -s /lib/libz.so libz.so

after this everything runs smoothly :-)

------------------------
All I did was link the /lib/libc.so.6 to /usr/lib and it worked


Thanks anyway

---


---
title: "Compilation error of fasta36 program: /usr/bin/ld: cannot find -lz"
date: 2013-11-14
forum: General Help
---

### Post by yogesh-gupta25 on 2013-11-14
I encountered with this error while attempted compiling fasta36 on my Ubuntu 12.04.3 64 bit machine:
  
/usr/bin/ld: cannot find -lz 
collect2: ld returned 1 exit status 
make: *** [fasta36] Error 1

  
I used following command: make -f ../make/Makefile.linux64_sse2

  I guessed it could be due to absence or broken symbolic link so tried  to find the correct file. I could see in my /usr/lib directory  following files:

lrwxrwxrwx 1 root root     16 Nov 18  2011 libzbar.so.0 -> libzbar.so.0.2.0
-rw-r--r-- 1 root root 187480 Nov 18  2011 libzbar.so.0.2.0
lrwxrwxrwx 1 root root     25 Nov 12 18:54 libzeitgeist-1.0.so.1 -> libzeitgeist-1.0.so.1.1.4
-rw-r--r-- 1 root root 122048 May  4  2012 libzeitgeist-1.0.so.1.1.4
lrwxrwxrwx 1 root root     18 Nov 12 18:54 libzephyr.so.4 -> libzephyr.so.4.0.0
-rw-r--r-- 1 root root  55672 Apr 30  2011 libzephyr.so.4.0.0
lrwxrwxrwx 1 root root     23 Nov 26  2010 libzvbi-chains.so.0 -> libzvbi-chains.so.0.0.0
-rw-r--r-- 1 root root  60112 Nov 26  2010 libzvbi-chains.so.0.0.0
lrwxrwxrwx 1 root root     17 Nov 26  2010 libzvbi.so.0 -> libzvbi.so.0.13.1
-rw-r--r-- 1 root root 546768 Nov 26  2010 libzvbi.so.0.13.1

I have no idea which one of these represent the -lz or how to fix this?  

Could someone help me sort this one out here? I appreciate your time and help.
  Thanks, 
Yogesh

---

### Post by steeldriver on 2013-11-14
'-lz' would expand to 'libz' which is the zlib compression library, I think. For development, you probably need to install the zlib1g**-dev** package

---

### Post by yogesh-gupta25 on 2013-11-14
Thanks much steeldriver!!
It worked :)

---


---
title: "Celtx crashing / freezing up, no joy :("
date: 2008-01-23
forum: General Help
---

### Post by Beowulf.1000 on 2008-01-23
I just downloaded and installed the tarball for the latest Celtx (Celtx 0.977) for Linux.  The usual download, extract here, cd to directory of extracted files, then ./celtx and Celtx loads, but then when choose either a sample screenplay or a template (FIlm, etc) it freezes up, and the terminal shows a great deal of odd output (full output attached as file, some output shown below. I have run Celtx on my system in the past, so this is really odd that it will not run correctly. Any ideas on how to get Celtx working on my system (Ubuntu 7.10).:

beowulf@ubuntu:~$ cd Desktop/celtx/
beowulf@ubuntu:~/Desktop/celtx$ ./celtx&
[1] 9006
beowulf@ubuntu:~/Desktop/celtx$ *** glibc detected *** ./celtx-bin: free(): invalid pointer: 0x0958d160 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb738ad65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb738e800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb78c8961]
./celtx-bin[0x82125ea]
./celtx-bin[0x8212dfc]
./celtx-bin[0x8211765]
./celtx-bin[0x826c6c3]
./celtx-bin[0x826baf9]
..
.. (many more pages of this sort of stuff)

---

### Post by Beowulf.1000 on 2008-01-23
> **Beowulf.1000 said:**
> I just downloaded and installed the tarball for the latest Celtx (Celtx 0.977) for Linux.  The usual download, extract here, cd to directory of extracted files, then ./celtx and Celtx loads, but then when choose either a sample screenplay or a template (FIlm, etc) it freezes up...

Well here is a rather odd addendum to my original post.  Frustrated at not being able to have Celtx on my Ubuntu 7.10 system, I thought hmmm what about wine, and the Windows version of Celtx? So I just downloaded the 0.977 Celtx for Windows and installed it on my linux system using wine and can run it with Wine and it seems to be working. Chalk one up for wine!  I still would like to get the native version of Celtx working for linux, but until the linux version issue is solved at least I can use Celtx.

---


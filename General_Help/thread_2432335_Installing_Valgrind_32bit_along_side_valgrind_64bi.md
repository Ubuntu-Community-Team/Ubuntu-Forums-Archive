---
title: "Installing Valgrind 32bit along side valgrind 64bit on ubuntu."
date: 2019-11-30
forum: General Help
---

### Post by FilesUnknown on 2019-11-30
I followed [http://www.linuxfromscratch.org/blfs/view/svn/general/valgrind.html](http://www.linuxfromscratch.org/blfs/view/svn/general/valgrind.html).
Which basically said: 
```
sed -i 's|/doc/valgrind||' docs/Makefile.in ./configure --prefix=/usr --datadir=/usr/share/doc/valgrind-3.15.0 
make
sudo make install
```
which does compile, but when I try to run a 64 bit steam program through wine it complains "/usr/bin/ld: i386:x86-64 architecture of input file `valgrind-m_debuglog.o' is incompatible with i386 output". Which I have no clue what it means other than maybe it checked what architecture I am and said nope. I have tried looking around for how to compile 32bit and all they say is throw [COLOR=#000000]--build=i686-pc-linux-gnu "CFLAGS=-m32" "CXXFLAGS=-m32" "LDFLAGS=-m32" flags at it.[/COLOR]
the output of trying to config>make>make install is: [https://github.com/EricKnaak/computerfacts/blob/master/Complile%2032bit%20valgrind%20on%20ubuntu%20AMD64](https://github.com/EricKnaak/computerfacts/blob/master/Complile%2032bit%20valgrind%20on%20ubuntu%20AMD64)
Hardware: [https://github.com/EricKnaak/computerfacts/blob/master/hardinfo_report.html](https://github.com/EricKnaak/computerfacts/blob/master/hardinfo_report.html) , [https://github.com/EricKnaak/computerfacts/blob/master/pc%20specs](https://github.com/EricKnaak/computerfacts/blob/master/pc%20specs)

Is this a ubuntu problem due to lack of multiarch or is this a valgrind, due to complaining about building arcoss arch? 
google is no help for cross compiled valgrind.
[https://www.google.com/search?q=cross+arch+valgrind&sxsrf=ACYBGNRw0AcXgCYfTsiiABahlCo7FFYBMA:1575146261363&ei=FdPiXeTdFbjC0PEP56msqAw&start=10&sa=N&ved=2ahUKEwikvIKL5ZLmAhU4ITQIHecUC8UQ8NMDegQIDBBA&biw=1373&bih=769](https://www.google.com/search?q=cross+arch+valgrind&sxsrf=ACYBGNRw0AcXgCYfTsiiABahlCo7FFYBMA:1575146261363&ei=FdPiXeTdFbjC0PEP56msqAw&start=10&sa=N&ved=2ahUKEwikvIKL5ZLmAhU4ITQIHecUC8UQ8NMDegQIDBBA&biw=1373&bih=769)

All I want to do is write info for this bug report! [https://bugs.winehq.org/show_bug.cgi?id=48197](https://bugs.winehq.org/show_bug.cgi?id=48197) The bug report is steam game in wine has a memory leak but not a leak on windows 10.
I have no idea how valgrind works. I knew how to type configure, make, install before this, but I have no clue whats going on after I hit make install. I have attempted to compile wine before but to no success building 32bit in 64 bit or was it 64 bit into 32 bit. So I am lost please help thanks.
Also 3.13 valgrind which comes packaged for ubuntu 18.04 has this problem :[https://bugs.kde.org/show_bug.cgi?id=414659](https://bugs.kde.org/show_bug.cgi?id=414659) . So I have to build 3.15 to have a chance of using valgrind on this steam game.

---


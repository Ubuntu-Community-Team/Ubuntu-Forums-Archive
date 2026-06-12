---
title: "TECkit installation from source code"
date: 2008-06-20
forum: General Help
---

### Post by wilson47 on 2008-06-20
Hello,

I have been trying to install teckit in Ubuntu Linux 8.04 with no success. I have followed the ./compile , make , make install route to installation with no success. I am always left with the message:

glen@dell-desktop:~/Desktop$ teckit_compile tex-text-long-s.map

teckit_compile: error while loading shared libraries: libTECkit_Compiler.so.0: cannot open shared object file: No such file or directory

I'm sorry, but this is the first time I've compiled a program by source and I don't know what to do from here.

Thanks for your help,

Glen M. W.

---

### Post by wilson47 on 2008-06-22
Bump...

---

### Post by dasunst3r on 2008-06-22
Before building, have you installed the necessary development packages?  You can install them by typing in the terminal *sudo apt-get install build-essential*.  I downloaded TECkit from [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=TECkitDownloads](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=TECkitDownloads) , did the procedures, and came out with no errors.

---

### Post by wilson47 on 2008-06-23
I do have build-essential installed and up to date. I also downloaded from that site as well. This is what I did explicitly, so hopefully someone can spot my error. 

1. Download tar ball
2. change rights to /usr/local/src using 
```
sudo chown yourusername /usr/local/src
sudo chmod u+rwx /usr/local/src
```
3. Move and unpack tar ball in /usr/local/src 
4. Move to new directory
5. Attempt to run ```
./configure 
```
6. It never actually worked for me just like that, so I usually change the rights using ```
sudo chmod 777 -R
``` to the whole directory, (since by this time I get rather frustrated)
7. I get ./configure to work. Everything seems to go fine
8. I run ```
make
```. Everything seems to go fine
9a. I then run ```
make install
```
9b. I then run ```
checkinstall
```
10. I think I get errors here... I am unable to get the output right now. I'll post back soon. 

Is this right thus far?

---

### Post by cariboo on 2008-06-23
You should run checkinstall instead of make, the script will do that for you.

Jim

---

### Post by wilson47 on 2008-06-23
So instead of 8--10 I should just run ```
checkinstall
``` ?
I'll give that a shot and post results later. Thanks!

---

### Post by wilson47 on 2008-06-23
I tried the above suggestion and this is my output:
```
glen@dell-desktop:/usr/local/src/TECkit_2_5_1$ checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
  Diese Software wurde unter der GNU GPL veröffentlicht


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Bereite Paket-Dokumentation vor...OK

Bitte geben Sie eine Beschreibung für das Paket ein.
Beenden Sie Ihre Beschreibung mit einer leeren Zeile oder EOF.
>> teckit compile .map to .tec and other such commands
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "TECkit_2_5_1" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

*** Warning: The package name "teckit_2_5_1" contains illegal.
*** Warning: characters. dpkg might not like that so I changed
*** Warning: them to dashes.

*** Warning: The package version "2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1" is not a
*** Warning: debian policy compliant one. Please specify an alternate one
2-5-1

Das Paket wird entsprechend dieser Vorgaben erstellt:

0 -  Maintainer: [ glen@dell-desktop ]
1 -  Summary: [ teckit compile .map to .tec and other such commands ]
2 -  Name:    [ teckit-2-5-1 ]
3 -  Version: [ 2-5-1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ TECkit_2_5_1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Geben Sie die betreffende Nummer ein, um die Vorgaben zu ändern: 

Installing with make install...

====================== Installations-Ergebnisse ==========================
Making install in lib
make[1]: Betrete Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3   -g -O2 -DNDEBUG -MT Compiler.lo -MD -MP -MF .deps/Compiler.Tpo -c -o Compiler.lo `test -f '../source/Compiler.cpp' || echo './'`../source/Compiler.cpp
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT Compiler.lo -MD -MP -MF .deps/Compiler.Tpo -c ../source/Compiler.cpp  -fPIC -DPIC -o .libs/Compiler.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT Compiler.lo -MD -MP -MF .deps/Compiler.Tpo -c ../source/Compiler.cpp -o Compiler.o >/dev/null 2>&1
mv -f .deps/Compiler.Tpo .deps/Compiler.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT adler32.lo -MD -MP -MF .deps/adler32.Tpo -c -o adler32.lo `test -f '../zlib-1.2.3/adler32.c' || echo './'`../zlib-1.2.3/adler32.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT adler32.lo -MD -MP -MF .deps/adler32.Tpo -c ../zlib-1.2.3/adler32.c  -fPIC -DPIC -o .libs/adler32.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT adler32.lo -MD -MP -MF .deps/adler32.Tpo -c ../zlib-1.2.3/adler32.c -o adler32.o >/dev/null 2>&1
mv -f .deps/adler32.Tpo .deps/adler32.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT compress.lo -MD -MP -MF .deps/compress.Tpo -c -o compress.lo `test -f '../zlib-1.2.3/compress.c' || echo './'`../zlib-1.2.3/compress.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT compress.lo -MD -MP -MF .deps/compress.Tpo -c ../zlib-1.2.3/compress.c  -fPIC -DPIC -o .libs/compress.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT compress.lo -MD -MP -MF .deps/compress.Tpo -c ../zlib-1.2.3/compress.c -o compress.o >/dev/null 2>&1
mv -f .deps/compress.Tpo .deps/compress.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT crc32.lo -MD -MP -MF .deps/crc32.Tpo -c -o crc32.lo `test -f '../zlib-1.2.3/crc32.c' || echo './'`../zlib-1.2.3/crc32.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT crc32.lo -MD -MP -MF .deps/crc32.Tpo -c ../zlib-1.2.3/crc32.c  -fPIC -DPIC -o .libs/crc32.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT crc32.lo -MD -MP -MF .deps/crc32.Tpo -c ../zlib-1.2.3/crc32.c -o crc32.o >/dev/null 2>&1
mv -f .deps/crc32.Tpo .deps/crc32.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT deflate.lo -MD -MP -MF .deps/deflate.Tpo -c -o deflate.lo `test -f '../zlib-1.2.3/deflate.c' || echo './'`../zlib-1.2.3/deflate.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT deflate.lo -MD -MP -MF .deps/deflate.Tpo -c ../zlib-1.2.3/deflate.c  -fPIC -DPIC -o .libs/deflate.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT deflate.lo -MD -MP -MF .deps/deflate.Tpo -c ../zlib-1.2.3/deflate.c -o deflate.o >/dev/null 2>&1
mv -f .deps/deflate.Tpo .deps/deflate.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT infback.lo -MD -MP -MF .deps/infback.Tpo -c -o infback.lo `test -f '../zlib-1.2.3/infback.c' || echo './'`../zlib-1.2.3/infback.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT infback.lo -MD -MP -MF .deps/infback.Tpo -c ../zlib-1.2.3/infback.c  -fPIC -DPIC -o .libs/infback.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT infback.lo -MD -MP -MF .deps/infback.Tpo -c ../zlib-1.2.3/infback.c -o infback.o >/dev/null 2>&1
mv -f .deps/infback.Tpo .deps/infback.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inffast.lo -MD -MP -MF .deps/inffast.Tpo -c -o inffast.lo `test -f '../zlib-1.2.3/inffast.c' || echo './'`../zlib-1.2.3/inffast.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inffast.lo -MD -MP -MF .deps/inffast.Tpo -c ../zlib-1.2.3/inffast.c  -fPIC -DPIC -o .libs/inffast.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inffast.lo -MD -MP -MF .deps/inffast.Tpo -c ../zlib-1.2.3/inffast.c -o inffast.o >/dev/null 2>&1
mv -f .deps/inffast.Tpo .deps/inffast.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inflate.lo -MD -MP -MF .deps/inflate.Tpo -c -o inflate.lo `test -f '../zlib-1.2.3/inflate.c' || echo './'`../zlib-1.2.3/inflate.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inflate.lo -MD -MP -MF .deps/inflate.Tpo -c ../zlib-1.2.3/inflate.c  -fPIC -DPIC -o .libs/inflate.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inflate.lo -MD -MP -MF .deps/inflate.Tpo -c ../zlib-1.2.3/inflate.c -o inflate.o >/dev/null 2>&1
mv -f .deps/inflate.Tpo .deps/inflate.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inftrees.lo -MD -MP -MF .deps/inftrees.Tpo -c -o inftrees.lo `test -f '../zlib-1.2.3/inftrees.c' || echo './'`../zlib-1.2.3/inftrees.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inftrees.lo -MD -MP -MF .deps/inftrees.Tpo -c ../zlib-1.2.3/inftrees.c  -fPIC -DPIC -o .libs/inftrees.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT inftrees.lo -MD -MP -MF .deps/inftrees.Tpo -c ../zlib-1.2.3/inftrees.c -o inftrees.o >/dev/null 2>&1
mv -f .deps/inftrees.Tpo .deps/inftrees.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT trees.lo -MD -MP -MF .deps/trees.Tpo -c -o trees.lo `test -f '../zlib-1.2.3/trees.c' || echo './'`../zlib-1.2.3/trees.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT trees.lo -MD -MP -MF .deps/trees.Tpo -c ../zlib-1.2.3/trees.c  -fPIC -DPIC -o .libs/trees.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT trees.lo -MD -MP -MF .deps/trees.Tpo -c ../zlib-1.2.3/trees.c -o trees.o >/dev/null 2>&1
mv -f .deps/trees.Tpo .deps/trees.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT uncompr.lo -MD -MP -MF .deps/uncompr.Tpo -c -o uncompr.lo `test -f '../zlib-1.2.3/uncompr.c' || echo './'`../zlib-1.2.3/uncompr.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT uncompr.lo -MD -MP -MF .deps/uncompr.Tpo -c ../zlib-1.2.3/uncompr.c  -fPIC -DPIC -o .libs/uncompr.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT uncompr.lo -MD -MP -MF .deps/uncompr.Tpo -c ../zlib-1.2.3/uncompr.c -o uncompr.o >/dev/null 2>&1
mv -f .deps/uncompr.Tpo .deps/uncompr.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3  -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT zutil.lo -MD -MP -MF .deps/zutil.Tpo -c -o zutil.lo `test -f '../zlib-1.2.3/zutil.c' || echo './'`../zlib-1.2.3/zutil.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT zutil.lo -MD -MP -MF .deps/zutil.Tpo -c ../zlib-1.2.3/zutil.c  -fPIC -DPIC -o .libs/zutil.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT zutil.lo -MD -MP -MF .deps/zutil.Tpo -c ../zlib-1.2.3/zutil.c -o zutil.o >/dev/null 2>&1
mv -f .deps/zutil.Tpo .deps/zutil.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3   -g -O2 -DNDEBUG -MT UnicodeNames.lo -MD -MP -MF .deps/UnicodeNames.Tpo -c -o UnicodeNames.lo `test -f '../source/UnicodeNames.cpp' || echo './'`../source/UnicodeNames.cpp
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT UnicodeNames.lo -MD -MP -MF .deps/UnicodeNames.Tpo -c ../source/UnicodeNames.cpp  -fPIC -DPIC -o .libs/UnicodeNames.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT UnicodeNames.lo -MD -MP -MF .deps/UnicodeNames.Tpo -c ../source/UnicodeNames.cpp -o UnicodeNames.o >/dev/null 2>&1
mv -f .deps/UnicodeNames.Tpo .deps/UnicodeNames.Plo
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2 -DNDEBUG  -no-undefined  -o libTECkit_Compiler.la -rpath /usr/local/lib Compiler.lo adler32.lo compress.lo crc32.lo deflate.lo infback.lo inffast.lo inflate.lo inftrees.lo trees.lo uncompr.lo zutil.lo UnicodeNames.lo  
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.2.3/crtbeginS.o  .libs/Compiler.o .libs/adler32.o .libs/compress.o .libs/crc32.o .libs/deflate.o .libs/infback.o .libs/inffast.o .libs/inflate.o .libs/inftrees.o .libs/trees.o .libs/uncompr.o .libs/zutil.o .libs/UnicodeNames.o  -L/usr/lib/gcc/i486-linux-gnu/4.2.3 -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.2.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libTECkit_Compiler.so.0 -o .libs/libTECkit_Compiler.so.0.0.0
(cd .libs && rm -f libTECkit_Compiler.so.0 && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so.0)
(cd .libs && rm -f libTECkit_Compiler.so && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so)
ar cru .libs/libTECkit_Compiler.a  Compiler.o adler32.o compress.o crc32.o deflate.o infback.o inffast.o inflate.o inftrees.o trees.o uncompr.o zutil.o UnicodeNames.o
ranlib .libs/libTECkit_Compiler.a
creating libTECkit_Compiler.la
(cd .libs && rm -f libTECkit_Compiler.la && ln -s ../libTECkit_Compiler.la libTECkit_Compiler.la)
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I../source/Public-headers -I../zlib-1.2.3   -g -O2 -DNDEBUG -MT Engine.lo -MD -MP -MF .deps/Engine.Tpo -c -o Engine.lo `test -f '../source/Engine.cpp' || echo './'`../source/Engine.cpp
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT Engine.lo -MD -MP -MF .deps/Engine.Tpo -c ../source/Engine.cpp  -fPIC -DPIC -o .libs/Engine.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../source/Public-headers -I../zlib-1.2.3 -g -O2 -DNDEBUG -MT Engine.lo -MD -MP -MF .deps/Engine.Tpo -c ../source/Engine.cpp -o Engine.o >/dev/null 2>&1
mv -f .deps/Engine.Tpo .deps/Engine.Plo
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2 -DNDEBUG  -no-undefined  -o libTECkit.la -rpath /usr/local/lib Engine.lo adler32.lo compress.lo crc32.lo deflate.lo infback.lo inffast.lo inflate.lo inftrees.lo trees.lo uncompr.lo zutil.lo  
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.2.3/crtbeginS.o  .libs/Engine.o .libs/adler32.o .libs/compress.o .libs/crc32.o .libs/deflate.o .libs/infback.o .libs/inffast.o .libs/inflate.o .libs/inftrees.o .libs/trees.o .libs/uncompr.o .libs/zutil.o  -L/usr/lib/gcc/i486-linux-gnu/4.2.3 -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.2.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libTECkit.so.0 -o .libs/libTECkit.so.0.0.0
(cd .libs && rm -f libTECkit.so.0 && ln -s libTECkit.so.0.0.0 libTECkit.so.0)
(cd .libs && rm -f libTECkit.so && ln -s libTECkit.so.0.0.0 libTECkit.so)
ar cru .libs/libTECkit.a  Engine.o adler32.o compress.o crc32.o deflate.o infback.o inffast.o inflate.o inftrees.o trees.o uncompr.o zutil.o
ranlib .libs/libTECkit.a
creating libTECkit.la
(cd .libs && rm -f libTECkit.la && ln -s ../libTECkit.la libTECkit.la)
make[2]: Betrete Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libTECkit_Compiler.la' '/usr/local/lib/libTECkit_Compiler.la'
/usr/bin/install -c .libs/libTECkit_Compiler.so.0.0.0 /usr/local/lib/libTECkit_Compiler.so.0.0.0
(cd /usr/local/lib && { ln -s -f libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so.0 || { rm -f libTECkit_Compiler.so.0 && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so.0; }; })
(cd /usr/local/lib && { ln -s -f libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so || { rm -f libTECkit_Compiler.so && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so; }; })
/usr/bin/install -c .libs/libTECkit_Compiler.lai /usr/local/lib/libTECkit_Compiler.la
/usr/bin/install -c .libs/libTECkit_Compiler.a /usr/local/lib/libTECkit_Compiler.a
chmod 644 /usr/local/lib/libTECkit_Compiler.a
chmod: changing permissions of `/usr/local/lib/libTECkit_Compiler.a': No such file or directory
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libTECkit.la' '/usr/local/lib/libTECkit.la'
/usr/bin/install -c .libs/libTECkit.so.0.0.0 /usr/local/lib/libTECkit.so.0.0.0
(cd /usr/local/lib && { ln -s -f libTECkit.so.0.0.0 libTECkit.so.0 || { rm -f libTECkit.so.0 && ln -s libTECkit.so.0.0.0 libTECkit.so.0; }; })
(cd /usr/local/lib && { ln -s -f libTECkit.so.0.0.0 libTECkit.so || { rm -f libTECkit.so && ln -s libTECkit.so.0.0.0 libTECkit.so; }; })
/usr/bin/install -c .libs/libTECkit.lai /usr/local/lib/libTECkit.la
/usr/bin/install -c .libs/libTECkit.a /usr/local/lib/libTECkit.a
chmod 644 /usr/local/lib/libTECkit.a
chmod: changing permissions of `/usr/local/lib/libTECkit.a': No such file or directory
make[2]: *** [install-libLTLIBRARIES] Fehler 1
make[2]: Verlasse Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
make: *** [install-recursive] Fehler 1

**** Installation fehlgeschlagen. Breche Paket-Erzeugung ab.

Räume auf...OK

Auf Wiedersehen!


```

Sorry for the German and the length. Should I go post on a German forum? :)

Just from my inspection, it looks like I'm having trouble towards the end in changing permissions while installing. I believe I read you can also run checkinstall with the option --install=no and then just install it yourself. Any thoughts??? I've been having simmilar permission problems elsewhere as well... Is there a way to reset privelages back to default (or something like that)? 

Thanks once again, I really appreciate it.

---

### Post by wilson47 on 2008-06-23
And just to confuse things even more, I have the following:
```
glen@dell-desktop:/usr/local/src/TECkit_2_5_1$ checkinstall --install=no

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
  Diese Software wurde unter der GNU GPL veröffentlicht



*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "TECkit_2_5_1" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

*** Warning: The package name "teckit_2_5_1" contains illegal.
*** Warning: characters. dpkg might not like that so I changed
*** Warning: them to dashes.

*** Warning: The package version "2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1
2.5.1" is not a
*** Warning: debian policy compliant one. Please specify an alternate one
2-5-1

Das Paket wird entsprechend dieser Vorgaben erstellt:

0 -  Maintainer: [ glen@dell-desktop ]
1 -  Summary: [ teckit compile .map to .tec and other such commands ]
2 -  Name:    [ teckit-2-5-1 ]
3 -  Version: [ 2-5-1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ TECkit_2_5_1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Geben Sie die betreffende Nummer ein, um die Vorgaben zu ändern: 

Installing with make install...

====================== Installations-Ergebnisse ==========================
Making install in lib
make[1]: Betrete Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
make[2]: Betrete Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libTECkit_Compiler.la' '/usr/local/lib/libTECkit_Compiler.la'
/usr/bin/install -c .libs/libTECkit_Compiler.so.0.0.0 /usr/local/lib/libTECkit_Compiler.so.0.0.0
(cd /usr/local/lib && { ln -s -f libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so.0 || { rm -f libTECkit_Compiler.so.0 && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so.0; }; })
(cd /usr/local/lib && { ln -s -f libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so || { rm -f libTECkit_Compiler.so && ln -s libTECkit_Compiler.so.0.0.0 libTECkit_Compiler.so; }; })
/usr/bin/install -c .libs/libTECkit_Compiler.lai /usr/local/lib/libTECkit_Compiler.la
/usr/bin/install -c .libs/libTECkit_Compiler.a /usr/local/lib/libTECkit_Compiler.a
chmod 644 /usr/local/lib/libTECkit_Compiler.a
chmod: changing permissions of `/usr/local/lib/libTECkit_Compiler.a': No such file or directory
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libTECkit.la' '/usr/local/lib/libTECkit.la'
/usr/bin/install -c .libs/libTECkit.so.0.0.0 /usr/local/lib/libTECkit.so.0.0.0
(cd /usr/local/lib && { ln -s -f libTECkit.so.0.0.0 libTECkit.so.0 || { rm -f libTECkit.so.0 && ln -s libTECkit.so.0.0.0 libTECkit.so.0; }; })
(cd /usr/local/lib && { ln -s -f libTECkit.so.0.0.0 libTECkit.so || { rm -f libTECkit.so && ln -s libTECkit.so.0.0.0 libTECkit.so; }; })
/usr/bin/install -c .libs/libTECkit.lai /usr/local/lib/libTECkit.la
/usr/bin/install -c .libs/libTECkit.a /usr/local/lib/libTECkit.a
chmod 644 /usr/local/lib/libTECkit.a
chmod: changing permissions of `/usr/local/lib/libTECkit.a': No such file or directory
make[2]: *** [install-libLTLIBRARIES] Fehler 1
make[2]: Verlasse Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/local/src/TECkit_2_5_1/lib'
make: *** [install-recursive] Fehler 1

**** Installation fehlgeschlagen. Breche Paket-Erzeugung ab.

Räume auf...OK

Auf Wiedersehen!

glen@dell-desktop:/usr/local/src/TECkit_2_5_1$ find /usr/local/src/TECkit_2_5_1/lib
/usr/local/src/TECkit_2_5_1/lib
/usr/local/src/TECkit_2_5_1/lib/compress.o
/usr/local/src/TECkit_2_5_1/lib/.libs
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.a
/usr/local/src/TECkit_2_5_1/lib/.libs/compress.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.lai
/usr/local/src/TECkit_2_5_1/lib/.libs/crc32.o
/usr/local/src/TECkit_2_5_1/lib/.libs/Engine.o
/usr/local/src/TECkit_2_5_1/lib/.libs/deflate.o
/usr/local/src/TECkit_2_5_1/lib/.libs/inftrees.o
/usr/local/src/TECkit_2_5_1/lib/.libs/trees.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.so.0.0.0
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.la
/usr/local/src/TECkit_2_5_1/lib/.libs/inffast.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.so.0
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.la
/usr/local/src/TECkit_2_5_1/lib/.libs/zutil.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.so
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.a
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.so.0.0.0
/usr/local/src/TECkit_2_5_1/lib/.libs/uncompr.o
/usr/local/src/TECkit_2_5_1/lib/.libs/inflate.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit_Compiler.lai
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.so.0
/usr/local/src/TECkit_2_5_1/lib/.libs/adler32.o
/usr/local/src/TECkit_2_5_1/lib/.libs/infback.o
/usr/local/src/TECkit_2_5_1/lib/.libs/Compiler.o
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.so
/usr/local/src/TECkit_2_5_1/lib/.libs/UnicodeNames.o
/usr/local/src/TECkit_2_5_1/lib/zutil.lo
/usr/local/src/TECkit_2_5_1/lib/uncompr.lo
/usr/local/src/TECkit_2_5_1/lib/inftrees.lo
/usr/local/src/TECkit_2_5_1/lib/crc32.o
/usr/local/src/TECkit_2_5_1/lib/trees.lo
/usr/local/src/TECkit_2_5_1/lib/Engine.o
/usr/local/src/TECkit_2_5_1/lib/deflate.o
/usr/local/src/TECkit_2_5_1/lib/inftrees.o
/usr/local/src/TECkit_2_5_1/lib/trees.o
/usr/local/src/TECkit_2_5_1/lib/libTECkit.la
/usr/local/src/TECkit_2_5_1/lib/inffast.o
/usr/local/src/TECkit_2_5_1/lib/UnicodeNames.lo
/usr/local/src/TECkit_2_5_1/lib/libTECkit_Compiler.la
/usr/local/src/TECkit_2_5_1/lib/zutil.o
/usr/local/src/TECkit_2_5_1/lib/compress.lo
/usr/local/src/TECkit_2_5_1/lib/.deps
/usr/local/src/TECkit_2_5_1/lib/.deps/adler32.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/inflate.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/zutil.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/UnicodeNames.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/deflate.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/infback.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/uncompr.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/trees.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/inffast.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/compress.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/Compiler.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/inftrees.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/crc32.Plo
/usr/local/src/TECkit_2_5_1/lib/.deps/Engine.Plo
/usr/local/src/TECkit_2_5_1/lib/inffast.lo
/usr/local/src/TECkit_2_5_1/lib/deflate.lo
/usr/local/src/TECkit_2_5_1/lib/Makefile
/usr/local/src/TECkit_2_5_1/lib/Makefile.am
/usr/local/src/TECkit_2_5_1/lib/uncompr.o
/usr/local/src/TECkit_2_5_1/lib/inflate.lo
/usr/local/src/TECkit_2_5_1/lib/crc32.lo
/usr/local/src/TECkit_2_5_1/lib/adler32.lo
/usr/local/src/TECkit_2_5_1/lib/inflate.o
/usr/local/src/TECkit_2_5_1/lib/adler32.o
/usr/local/src/TECkit_2_5_1/lib/infback.o
/usr/local/src/TECkit_2_5_1/lib/Compiler.o
/usr/local/src/TECkit_2_5_1/lib/infback.lo
/usr/local/src/TECkit_2_5_1/lib/Makefile.in
/usr/local/src/TECkit_2_5_1/lib/Engine.lo
/usr/local/src/TECkit_2_5_1/lib/UnicodeNames.o
/usr/local/src/TECkit_2_5_1/lib/Compiler.lo


```

The last few lines CLEARLY show there is such a directory that chmod is looking for to change the permission of. So I'm thinking this is a more permission related problem???

---

### Post by wilson47 on 2008-06-23
OOPS! I guess it wasn't so clearly after all. chmod is looking for 
```
/usr/local/lib/libTECkit.a

```

but everything is actually in 

```
/usr/local/src/TECkit_2_5_1/lib/.libs/libTECkit.a

```

So how can I fix this??? Does this have something to do with 

```
./configure --prefix=/usr
```???

(Just quoting from [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo))

---

### Post by wilson47 on 2008-06-24
What if I were to change the permission on ```
/usr/local/lib/
``` to be 777 or something like that? Could that work??? 

Any ideas would be helpful and much appreciated! Thanks!!!

---

### Post by wilson47 on 2008-06-24
This is the part that confuses me:
```
/usr/bin/install -c .libs/libTECkit_Compiler.a /usr/local/lib/libTECkit_Compiler.a
chmod 644 /usr/local/lib/libTECkit_Compiler.a
chmod: changing permissions of `/usr/local/lib/libTECkit_Compiler.a': No such file or directory
```
It looks as if in the first line it is trying to install /usr/local/lib/libTECkit_Compiler.a and then in the next line it is trying to change permissions of this file which was just created, but then no such file can be found... 

I am guessing this is where the problem is stemming from, the unability to change permissions of these files? Or in the creation of them?

---

### Post by wilson47 on 2008-06-24
help please!

---


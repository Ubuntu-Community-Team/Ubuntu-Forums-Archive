---
title: "help install tgz game"
date: 2007-01-23
forum: General Help
---

### Post by DougieFresh4U on 2007-01-23
I have downloaded a game from "The Linux Tome" called Mahjong. I can never get zip or tar files installed. Could some one please help with some code work to ionstall please. i believe it's in temp folder and  downloaded file is  **mahjong_lin.tgz**Thanks to any one willing to help me out=D>

---

### Post by matthewstory on 2007-01-23
cd /tmp
tar vzxf mahjong.tgz

and for gzip files
gunzip name.gz

---

### Post by punx45 on 2007-01-23
but that only unpacks the tar.  and probably what is in that particular tarball is the source code for the game which you now have to compile and install. 

installing from source is a pain.  check synaptic, or look for .deb packages before you resort to source.   unless you are using source for a specific reason.

[see here for details on compiling and installing source]("http://www.psychocats.net/ubuntu/installingsoftware").  (its near the bottom of the page)

---

### Post by DougieFresh4U on 2007-01-24
> **punx45 said:**
> but that only unpacks the tar.  and probably what is in that particular tarball is the source code for the game which you now have to compile and install. 

installing from source is a pain.  check synaptic, or look for .deb packages before you resort to source.   unless you are using source for a specific reason.

[see here for details on compiling and installing source]("http://www.psychocats.net/ubuntu/installingsoftware").  (its near the bottom of the page)
The game came from the "The Linux Tome" and it only come that way. I tried the code, maybe I did it wrong but this is what came back:dougie@DougiesToyBox:~$ cd /tmp
dougie@DougiesToyBox:/tmp$ tar vzxf mahjong.tgz
tar: mahjong.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dougie@DougiesToyBox:/tmp$ 
Thanks for replies=D>

---

### Post by matthewstory on 2007-01-24
right than the file isnt' in the /tmp directory . . . you need to find the right directory and cd to it.  Once the tar is unpacked you probably need to compile from source, although it's entirely possible that the file is a pre-compiled binary in which case you just run the binary.  But if you need to install from source it'll go something like this:

cd Mahjohngg

or whatever the folder is

then 

./Configure

or

./configure

then

make
make install

that should do it for you man.

---

### Post by aysiu on 2007-01-24
There are a whole bunch of Mahjong programs in the repositories--ones you don't have to install from source:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mahjong&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mahjong&searchon=name&subword=1&version=all&release=all)

---

### Post by DougieFresh4U on 2007-01-24
> **aysiu said:**
> There are a whole bunch of Mahjong programs in the repositories--ones you don't have to install from source:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mahjong&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mahjong&searchon=name&subword=1&version=all&release=all)

Hello aysiu, long time no see):P Question, are those all not the same or are they different games and can I use only ones pertaining to Feisty? I already have the 2 from the Add/Remove list>mahjong & Kmahjong. I just wanted a variety. i have a game on my XP machine from Game House that has over 300 different layouts. So I thought I would give these ones I saw on "The Linux Tome" a shot as the 2 I have do not give much of a variety. thanks for your suggestion. The second one I just downloaded but cannot open is: xmahjongg-3.5.tar.gz and I believe it went to temp folder

---

### Post by matthewstory on 2007-01-24
if you want help with this right now AIM me at: codewarrior16 and i'll try to help you through the installs on these . . . as this will probably take a long time over the forum

---

### Post by DougieFresh4U on 2007-01-24
dougie@DougiesToyBox:/tmp$ ls xmahjongg-3.5
acconfig.h    counter.cc  hint.cc      matches.hh     share         tileset.cc
aclocal.m4    counter.hh  hint.hh      missing        solution.cc   tileset.hh
alarm.cc      fmalloc.c   images       mkinstalldirs  solution.hh   traverse.cc
alarm.hh      game.cc     INSTALL      moment.cc      solvable.cc   traverse.hh
board.cc      game.hh     install-sh   moment.hh      solvable.hh   vector.cc
board.hh      giffunc.c   kdets.cc     NEWS           stamp-h.in    vector.hh
button.cc     gif.h       kdets.hh     panel.cc       strerror.c    vectori.cc
button.hh     gifread.c   kmjts.cc     panel.hh       swgeneral.cc  xmahjongg.6
clp.c         giftoc.c    kmjts.hh     permstr.cc     swgeneral.hh  xmj3ts.cc
clp.h         gifx.c      main.cc      permstr.hh     swwidget.cc   xmj3ts.hh
config.h.in   gifx.h      Makefile.am  random.cc      swwidget.hh
configure     gmjts.cc    Makefile.in  README         tile.cc
configure.in  gmjts.hh    matches.cc   rpm.spec       tile.hh
dougie@DougiesToyBox:/tmp$

---

### Post by DougieFresh4U on 2007-01-24
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$ make
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c clp.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c fmalloc.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c giffunc.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c gifread.c
gcc -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c gifx.c
c++ -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c permstr.cc
c++ -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c vectori.cc
vector.hh:8: error: ‘void* operator new(size_t, void*)’ may not be declared as static
make: *** [vectori.o] Error 1
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$

---

### Post by DougieFresh4U on 2007-01-24
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$ sudo make
c++ -Wall -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c vectori.cc
vector.hh:8: error: ‘void* operator new(size_t, void*)’ may not be declared as static
make: *** [vectori.o] Error 1
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$

---

### Post by DougieFresh4U on 2007-01-24
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$ sudo aptitude search xmahjongg
i   xmahjongg                                              - tile-based solitaire game                                       
dougie@DougiesToyBox:/usr/local/xmahjongg-3.5$

---

### Post by DougieFresh4U on 2007-01-24
dougie@DougiesToyBox:/usr/local$ cd Mah_MahJong
bash: cd: Mah_MahJong: No such file or directory
dougie@DougiesToyBox:/usr/local$ ./Mah
bash: ./Mah: No such file or directory
dougie@DougiesToyBox:/usr/local$ ./Mah_MahJong
bash: ./Mah_MahJong: No such file or directory
dougie@DougiesToyBox:/usr/local$

---


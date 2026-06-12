---
title: "problem with make"
date: 2008-04-30
forum: General Help
---

### Post by badee on 2008-04-30
Hello how r u guys

I turned from win to linux about 6 months ago and I'm very happy but there is something drive me crazy every single time I tried to make some stupid software it tell me some thing like this:
 make: *** error

even when I installed build-essential , make ,g++, even kdevelop

now I'm trying to install dmg2iso from here [http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)
and it needs make every time I try to make it it tells me:


> rm -f *.o dmg2iso.exe 
gcc -O3 -c dmg2iso.cc
dmg2iso.h:45: error: ‘__int32’ does not name a type
dmg2iso.cc: In function ‘int main(int, char**)’:
dmg2iso.cc:117: error: ‘__int32’ does not name a type
dmg2iso.cc:122: error: ‘__int32’ does not name a type
dmg2iso.cc:123: error: ‘__int32’ does not name a type
dmg2iso.cc:124: error: ‘block_type’ was not declared in this scope
dmg2iso.cc:126: error: ‘out_offs’ was not declared in this scope
dmg2iso.cc:127: error: ‘out_size’ was not declared in this scope
dmg2iso.cc:128: error: ‘in_offs’ was not declared in this scope
dmg2iso.cc:129: error: ‘in_size’ was not declared in this scope
dmg2iso.cc:130: error: ‘convert_endian’ was not declared in this scope
dmg2iso.cc:140: error: ‘last_offs’ was not declared in this scope
dmg2iso.cc:158: error: ‘last_in_offs’ was not declared in this scope
dmg2iso.cc:161: error: ‘last_offs’ was not declared in this scope
dmg2iso.cc:172: error: ‘last_offs’ was not declared in this scope
dmg2iso.cc:172: error: ‘last_in_offs’ was not declared in this scope
make: *** [dmg2iso.o] Error 1


what should I do please  thank you

---

### Post by Monicker on 2008-04-30
> **badee said:**
> Hello how r u guys

I turned from win to linux about 6 months ago and I'm very happy but there is something drive me crazy every single time I tried to make some stupid software it tell me some thing like this:
 make: *** error

even when I installed build-essential , make ,g++, even kdevelop

now I'm trying to install dmg2iso from here [http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)
and it needs make every time I try to make it it tells me:




what should I do please  thank you


Looks like an issue which should be taken up with the developers of the application.

---

### Post by badee on 2008-04-30
> **Monicker said:**
> Looks like an issue which should be taken up with the developers of the application.

I'll give it a shot thanx dude :)

---

### Post by niteshifter on 2008-04-30
Hi, 

__int32 is Windows-speak. You could download the perl script from that site - I gave it a quick glance, you'll need to grab the package

libcompress-zlib-perl

from the repos to make it work.

---

### Post by badee on 2008-04-30
thanx niteshifter and Monicker

Ok that good thank god

I did this and now it's work correctly:

> sudo apt-get install libcompress-zlib-perl

>     cd /usr/bin

    sudo wget [http://www.blinkenlights.ch/gnupod/dmg2iso.pl](http://www.blinkenlights.ch/gnupod/dmg2iso.pl)


> sudo gedit dmg2iso.pl

At the very top you should see a line that says &#8216;#!/usr/local/bin/perl&#8216;. This tells the script where to find perl. On my installation, perl is located in &#8216;/usr/bin/perl&#8216;. So change that line if you need to.


Now let&#8217;s make it excecutable.

> sudo chmod 777 dmg2iso.pl

> cd

finally

> dmg2iso.pl file.dmg file.iso

no need for make and the problem not in make but in the file that I'm trying to make it

thanx guys soo much

---


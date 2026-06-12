---
title: "error installing ndiswrapper-1.2"
date: 2005-08-07
forum: General Help
---

### Post by JoeM on 2005-08-07
I receive the following with Step 3 of the HOWTO [http://www.ubuntuforums.org/showthread.php?t=31926&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=31926&page=1&pp=10)



[I]joe@laptop:~/Desktop/ndiswrapper-1.2$ sudo make
make -C driver
make[1]: Entering directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/joe/Desktop/ndiswrapper-1. 2/driver \
        NDISWRAPPER_VERSION=1.2 \
        EXTRA_VERSION= modules
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 11: gcc: comman d not found
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 12: gcc: comman d not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/joe/Desktop/ndiswrapper-1.2/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/joe/Desktop/ndiswrapper-1.2/driver/hal.o] Error 127
make[2]: *** [_module_/home/joe/Desktop/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make: *** [all] Error 2
joe@laptop:~/Desktop/ndiswrapper-1.2$ sudo make install
make -C driver install
make[1]: Entering directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/joe/Desktop/ndiswrapper-1. 2/driver \
        NDISWRAPPER_VERSION=1.2 \
        EXTRA_VERSION= modules
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 11: gcc: comman d not found
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 12: gcc: comman d not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/joe/Desktop/ndiswrapper-1.2/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/joe/Desktop/ndiswrapper-1.2/driver/hal.o] Error 127
make[2]: *** [_module_/home/joe/Desktop/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make: *** [install] Error 2[/I]

---

### Post by shockertwin on 2005-08-08
[QUOTE=JoeM]I receive the following with Step 3 of the HOWTO [http://www.ubuntuforums.org/showthread.php?t=31926&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=31926&page=1&pp=10)



[I]joe@laptop:~/Desktop/ndiswrapper-1.2$ sudo make
make -C driver
make[1]: Entering directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/joe/Desktop/ndiswrapper-1. 2/driver \
        NDISWRAPPER_VERSION=1.2 \
        EXTRA_VERSION= modules
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 11: gcc: comman d not found
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 12: gcc: comman d not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/joe/Desktop/ndiswrapper-1.2/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/joe/Desktop/ndiswrapper-1.2/driver/hal.o] Error 127
make[2]: *** [_module_/home/joe/Desktop/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make: *** [all] Error 2
joe@laptop:~/Desktop/ndiswrapper-1.2$ sudo make install
make -C driver install
make[1]: Entering directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/joe/Desktop/ndiswrapper-1. 2/driver \
        NDISWRAPPER_VERSION=1.2 \
        EXTRA_VERSION= modules
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 11: gcc: comman d not found
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 12: gcc: comman d not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/joe/Desktop/ndiswrapper-1.2/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/joe/Desktop/ndiswrapper-1.2/driver/hal.o] Error 127
make[2]: *** [_module_/home/joe/Desktop/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joe/Desktop/ndiswrapper-1.2/driver'
make: *** [install] Error 2[/I][/QUOTE]
 do the following:

sudo apt-get install gcc

i forget the version i think it is gcc-3.3. if you do the above command it will give you a list of options. After installing gcc, try recompiling.

---

### Post by JoeM on 2005-08-08
[QUOTE=shockertwin]do the following:

sudo apt-get install gcc

i forget the version i think it is gcc-3.3. if you do the above command it will give you a list of options. After installing gcc, try recompiling.[/QUOTE]


Great, that worked, and i was able to then install NDIS.  But, now I am having an issue with the driver.  I found on the ndis wiki that my card (d-link DWL-650  [not the G or the +, just the basic 650]) should use the XP driver from the d-link site.  So that is what i downloaded and placed the INF on the desktop.

This is the message i get though

[I]joe@laptop:~/Desktop$ sudo ndiswrapper -i NETR33X.INF
Installing netr33x
joe@laptop:~/Desktop$ sudo ndiswrapper -l
Installed ndis drivers:
netr33x invalid driver![/I]

---

### Post by Takis on 2005-08-09
There's some .sys file that comes with the .inf file. I'm not sure if it's supplied on the ndiswrapper website because I don't have that model card. Try using the one off the cd, it'll be in the same directory as the .inf on the cd.

The .sys file needs to be in the same directory as the .inf file.

---

### Post by JoeM on 2005-08-09
I had the sys file there too.

I suppose if I need an excuse to get a new G router/card then this is it.  Or at least a new B card that works with Ubuntu without windows drivers and NDIS.  I will search the boards for what works, I would like to be able to just insert the card and connect.

---

### Post by Takis on 2005-08-10
Fair enough.

I don't want to insist, but try double-checking that when you try to install the inf that the sys is in the same directory. It's just that both my friend and I had the exact same error message and it was because the sys file wasn't in the same dir.

---

### Post by blu.gecko on 2005-08-10
the  way I had to figure out which file to use is to copy the info down from the hardware properties from MS before the install, atleast thats how I did it, I backed up all my linux jazz and installed xp with a quick format, installed the exe, then looked on the driver signing. if you have to many issues figuring out which file it is you could always try that.

blu :-# 

UBER........Ubuntu User....6months now

---

### Post by TheVirginian on 2005-10-20
Did you make sure you got the exact right driver for your card as there are 4 different cards and drivers with the exact model # but with different version numbers, ex. mine is vP1. Also do not cheat and use the drivers off of the disk for your card as they usually will not work, make sure you get the downloaded ones from the dlink site. These are some of the things I recently learned the hard way, I'm sure there are more. I found a good list of cards and what drivers work best with them but I'll be darned if I can remember where, hopefully somebody else can tell you. Sorry I cant be more help.

Mike

---


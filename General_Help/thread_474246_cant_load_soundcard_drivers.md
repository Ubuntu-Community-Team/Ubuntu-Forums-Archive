---
title: "cant load soundcard drivers"
date: 2007-06-14
forum: General Help
---

### Post by bruce1354 on 2007-06-14
I have been following the steps in the  Comprehensive Sound Problem Solutions Guide v0.5e ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) and I find that I cannot load the driver for my sound card with modprobe, using module-assistant or without. 

I have a fresh install of Fiesty and I don't know where to go from here.

My soundcard is a Crystal cs4281

The most perplexing thing to me is when I follow the steps to do this:

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=cs4281 --with-oss=yes 

I get back this:

sudo: ./configure: command not found

Any insight?

---

### Post by Gruelius on 2007-06-15
```
 cd /usr/src sudo tar xjvf alsa-driver.tar.bz2 cd modules/alsa-driver
```
Are you in  the /usr/src/modules/asla-driver directory? Paste the contents of it please if you are

---

### Post by bruce1354 on 2007-06-15
Thanks

No I wasn't but when I moved there and ran sudo make it gives errors. Do you still want to see the contents of the directory?





river  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/include/adriver.h:858,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h:541: error: expected identifier or ‘(’ before numeric constant
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

---


---
title: "help with makedrv"
date: 2008-04-26
forum: General Help
---

### Post by elmaxx on 2008-04-26
hello all, the problem im having is with a modified driver i managed to secure from looking at the ubuntu forums.

here's my wifi info...
vendor id: 0xbda (Realtek Semiconductor)
product id: 0x8189

back in 7.10 i would run a ./makedrv to ready the driver, and then another command included in the package to get it going... but since i updated to 8.04 the  following happens when i run the ./makedrv command to get the driver going, hence i have no wifi...

elmaxx@Snort:~/drivers/modified$ sudo ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/elmaxx/.local/share/Trash/files/modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/elmaxx/.local/share/Trash/files/modified/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/elmaxx/.local/share/Trash/files/modified/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/elmaxx/.local/share/Trash/files/modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/elmaxx/.local/share/Trash/files/modified/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/elmaxx/.local/share/Trash/files/modified/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2


Any help solving this will be greatly apreciated, thanks!

---

### Post by elmaxx on 2008-04-26
went to this site... 
 
[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) 
 
and tried downloading the patched drivers... but the makedrv command won't work... this is the output... 
 
elmaxx@Snort:~/drivers/rtl8187b-modified$ sudo ./makedrv 
sudo: ./makedrv: command not found 
 
i'm very new to linux... please help.

---

### Post by elmaxx on 2008-04-27
i thought at first that maybe the 7.10 upgrade had somehow gone wrong, so i installed 8.04 cleanly, i noticed that some scripts lacked the "is executable" permission, but, since my xorg.conf file (gateway 6720) didnt have the 7.10 modifications i needed for the video support i had to reinstall 7.10, fix the file and update, then once again with 8.04 on my system, i gave all the files in the new tar'd drivers executable permissions, and my wifi is working again :D

Thank you guys!

i just hope this note reaches Mr. Cuervo, so he can put the correct permissions on his files, newbies as me may have a very difficult time figuring things out :)


have a great day.

---


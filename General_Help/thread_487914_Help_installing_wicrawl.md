---
title: "Help installing wicrawl"
date: 2007-06-29
forum: General Help
---

### Post by xspazxd on 2007-06-29
There's no configure file, and I keep getting errors but I have the prerequisits. Does it matter if I have a higher version of something it calls for?

> randy@randy-laptop:~$ su
Password: 
root@randy-laptop:/home/randy# cd '/home/randy/Desktop/wicrawl'
root@randy-laptop:/home/randy/Desktop/wicrawl# ./configure
bash: ./configure: No such file or directory
root@randy-laptop:/home/randy/Desktop/wicrawl# ./install
bash: ./install: No such file or directory
root@randy-laptop:/home/randy/Desktop/wicrawl# make
make[1]: Entering directory `/home/randy/Desktop/wicrawl/util'
rm -f libutil.a errlib.o util.o ~* .deps
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/util'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/discovery'
rm -f apcore base64.o discovery.o version.o hash.o ../util/libutil.a linux.o ~* .deps
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/discovery'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/plugins'
make[2]: Entering directory `/home/randy/Desktop/wicrawl/plugins/aircrack-wep-cracking/aircrack-ng-0.6.1'
rm -f aireplay-ng airodump-ng aircrack-ng airdecap-ng arpforge-ng ivstools kstats makeivs aircrack-ng-opt-prof_gen aircrack-ng-opt aircrack-ng-opt-prof prof/*
make[2]: Leaving directory `/home/randy/Desktop/wicrawl/plugins/aircrack-wep-cracking/aircrack-ng-0.6.1'
make[2]: Entering directory `/home/randy/Desktop/wicrawl/plugins/cowpatty-wpa-psk-bruteforce/cowpatty'
rm -f md5.o sha1.o utils.o cowpatty.o genpmk.o cowpatty genpmk *~
make[2]: Leaving directory `/home/randy/Desktop/wicrawl/plugins/cowpatty-wpa-psk-bruteforce/cowpatty'
make[2]: Entering directory `/home/randy/Desktop/wicrawl/plugins/weplab-bruteforce/weplab-0.1.5'
test -z "weplab" || rm -f weplab
rm -f *.o core *.core
make[2]: Leaving directory `/home/randy/Desktop/wicrawl/plugins/weplab-bruteforce/weplab-0.1.5'
make[2]: Entering directory `/home/randy/Desktop/wicrawl/plugins/pickupline/pul'
rm -f *.o pul
make[2]: Leaving directory `/home/randy/Desktop/wicrawl/plugins/pickupline/pul'
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/plugins'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/util/dhcp'
No build directory for linux-2.2 - please run ./configure.
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/util/dhcp'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/util'
Makefile:25: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/util'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/util'
make[1]: `.deps' is up to date.
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/util'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/discovery'
Makefile:45: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/discovery'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/discovery'
make[1]: `.deps' is up to date.
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/discovery'
make[1]: Entering directory `/home/randy/Desktop/wicrawl/util'
cc -g -Wall -I../include -I.   -c -o errlib.o errlib.c
In file included from ../include/wicrawl.h:79,
                 from errlib.c:1:
/usr/include/linux/wireless.h:646: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:659: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:684: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:700: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:713: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:740: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:802: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:838: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:847: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:859: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:882: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:897: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:941: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1042: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1060: error: expected specifier-qualifier-list before ‘__u16’
In file included from ../include/wicrawl.h:96,
                 from errlib.c:1:
../include/discovery.h:109: warning: ‘packed’ attribute ignored for field of type ‘uint8_t[16]’
../include/discovery.h:110: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:111: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:112: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:113: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:114: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:115: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:116: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:117: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:118: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:119: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
make[1]: *** [errlib.o] Error 1
make[1]: Leaving directory `/home/randy/Desktop/wicrawl/util'
make: *** [wicrawl] Error 2
root@randy-laptop:/home/randy/Desktop/wicrawl# make install

-e Starting wicrawl installation:

Installing base files in:   [/usr/local/wicrawl]
Installing binaries in:     [/usr/sbin]
Installing config files in: [/etc/wicrawl]
Installing docs in:         [/usr/share/doc/wicrawl]

# Directories, perl modules, and conf files
/usr/bin/install: cannot stat `discovery/apcore': No such file or directory
make: *** [install] Error 1
root@randy-laptop:/home/randy/Desktop/wicrawl# 


I've spent almost 4 days trying to get this thing to work. It's bugging me. Someone please help. Thanks in advance

---

### Post by xspazxd on 2007-06-30
I still need help..

---

### Post by jimmyccs001 on 2007-07-02
I also got the same error when compiling AODV-UU-0.9.3.
Someone please help.

In file included from main.c:30:
/usr/include/linux/wireless.h:646: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:659: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:684: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:700: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:713: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:740: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:802: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:838: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:847: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:859: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:882: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:897: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:941: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1042: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1060: error: expected specifier-qualifier-list before ‘__u16’
main.c: In function ‘get_if_info’:
main.c:235: error: storage size of ‘ifr’ isn’t known
main.c:235: warning: unused variable ‘ifr’
main.c: In function ‘host_init’:
main.c:337: error: storage size of ‘ifc’ isn’t known
main.c:338: error: storage size of ‘ifreq’ isn’t known
main.c:354: error: invalid application of ‘sizeof’ to incomplete type ‘struct ifreq’ 
main.c:354: error: increment of pointer to unknown structure
main.c:354: error: arithmetic on pointer to an incomplete type
main.c:357: error: ‘struct iwreq’ has no member named ‘ifr_name’
main.c:357: error: dereferencing pointer to incomplete type
main.c:359: error: dereferencing pointer to incomplete type
main.c:338: warning: unused variable ‘ifreq’
main.c:337: warning: unused variable ‘ifc’
make: *** [main.o] Error 1
[/PHP][/PHP][/PHP][/PHP]

---

### Post by xof7 on 2007-07-31
bump
I'm getting the same problem

```
jeff@article7:~/Desktop/wicrawl-0.3a$ sudo make
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util'
Makefile:25: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util'
rm -f libutil.a errlib.o util.o ~* .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
Makefile:45: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
rm -f apcore base64.o discovery.o version.o hash.o ../util/libutil.a linux.o ~* .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/plugins'
make[2]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/aircrack-wep-cracking/aircrack-ng-0.6.1'
rm -f aireplay-ng airodump-ng aircrack-ng airdecap-ng arpforge-ng ivstools kstats makeivs aircrack-ng-opt-prof_gen aircrack-ng-opt aircrack-ng-opt-prof prof/*
make[2]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/aircrack-wep-cracking/aircrack-ng-0.6.1'
make[2]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/cowpatty-wpa-psk-bruteforce/cowpatty'
rm -f md5.o sha1.o utils.o cowpatty.o genpmk.o cowpatty genpmk *~
make[2]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/cowpatty-wpa-psk-bruteforce/cowpatty'
make[2]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/weplab-bruteforce/weplab-0.1.5'
test -z "weplab" || rm -f weplab
rm -f *.o core *.core
make[2]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/weplab-bruteforce/weplab-0.1.5'
make[2]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/pickupline/pul'
rm -f *.o pul
make[2]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/plugins/pickupline/pul'
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/plugins'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util/dhcp'
No build directory for linux-2.2 - please run ./configure.
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util/dhcp'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util'
Makefile:25: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make[1]: `.deps' is up to date.
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
Makefile:45: .deps: No such file or directory
gcc -g -Wall -I../include -I. -MM *.c > .deps
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
make[1]: `.deps' is up to date.
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/discovery'
make[1]: Entering directory `/home/jeff/Desktop/wicrawl-0.3a/util'
cc -g -Wall -I../include -I.   -c -o errlib.o errlib.c
In file included from ../include/wicrawl.h:79,
                 from errlib.c:1:
/usr/include/linux/wireless.h:646: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:659: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:684: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:700: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:713: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:740: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:802: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:838: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:847: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:859: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:882: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:897: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:941: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1042: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1060: error: expected specifier-qualifier-list before ‘__u16’
In file included from ../include/wicrawl.h:96,
                 from errlib.c:1:
../include/discovery.h:109: warning: ‘packed’ attribute ignored for field of type ‘uint8_t[16]’
../include/discovery.h:110: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:111: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:112: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:113: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:114: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:115: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:116: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:117: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:118: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
../include/discovery.h:119: warning: ‘packed’ attribute ignored for field of type ‘p80211item_uint32_t’
make[1]: *** [errlib.o] Error 1
make[1]: Leaving directory `/home/jeff/Desktop/wicrawl-0.3a/util'
make: *** [wicrawl] Error 2

```

---

### Post by einfinger on 2008-07-02
im having the same problem, someone must know how to get this to work ?

---

### Post by Ptero-4 on 2008-07-02
Does it have a file called autogen. If it have one you need to run ./autogen and it creates the ./configure file.

---

### Post by einfinger on 2008-07-03
no it doesnt have autogen

---


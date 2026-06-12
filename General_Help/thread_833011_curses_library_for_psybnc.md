---
title: "curses library for psybnc"
date: 2008-06-18
forum: General Help
---

### Post by ahbb on 2008-06-18
Hi there,

Iv installed psybnc on my linux box that have ubuntu on.

I did exactly as what the website say.

But now I get this error.

root@lekkerlag:~/psybnc/psybnc# make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
[*] Running Autoconfig.
System: Linux
Socket Libs: Internal.
Environment: Internal.
Time-Headers: in time.h and sys/time.h
Byte order: Big Endian.
IPv6-Support: Yes.
async-DNS-Support: Yes.
SSL-Support: Yes.
Creating Makefile
Random Seed created.
[*] Creating Menu, please wait.
This needs the ncurses library. If it is not available, menuconf wont work. If you are using curses, use make menuconfig-curses instead.
make: *** [menuconfig] Error 1

I see there is so much ncurses to install, can you please tell me which one i must use so that i can config the psybnc?

Thanks

Andrew

---

### Post by arunsonnet on 2010-06-12
I used *libncurses5-dev* and it compiled without any problem :)

---


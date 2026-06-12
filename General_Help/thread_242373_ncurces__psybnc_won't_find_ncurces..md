---
title: "ncurces / psybnc won't find ncurces."
date: 2006-08-23
forum: General Help
---

### Post by woofcat on 2006-08-23
```
jim@jim-desktop:~/Desktop/psybnc$ sudo apt-get install ncurses-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim-desktop:~/Desktop/psybnc$ make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
Using existent configuration File.
[*] Running Autoconfig.
System: Linux
Socket Libs: Internal.
Environment: Internal.
Time-Headers: in time.h and sys/time.h
Byte order: Big Endian.
IPv6-Support: Yes.
async-DNS-Support: No, using blocking DNS.
SSL-Support: No openssl found. Get openssl at www.openssl.org
Creating Makefile
[*] Creating Menu, please wait.
This needs the ncurses library. If it is not available, menuconf wont work. If you are using curses, use make menuconfig-curses instead.
make: *** [menuconfig] Error 1

```

For me it just dosn't work :(
Does anyone have any idea's?

---

### Post by woofcat on 2006-08-24
I also linked libncurses.so.5.5 to libncurses.so it did not help.

---

### Post by crackseller on 2006-08-24
Edited: I didn't read correctly. I honestly don't know ... sorry man. You did install the ncurses (not -dev) package though, did you?

---

### Post by woofcat on 2006-08-25
Thanks for trying anyways. I hoped someone on here could help me out but it dosn't look that way :(

---

### Post by madmonk3y on 2007-06-12
sudo apt-get install ncurses-base ncurses-bin ncurses-term libncurses5 libncurses5-dev.

That should do the trick.

[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---


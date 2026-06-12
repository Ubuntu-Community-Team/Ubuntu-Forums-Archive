---
title: "LibNXT for Lego Mindstorms won't compile with scons"
date: 2013-08-17
forum: General Help
---

### Post by blesbok on 2013-08-17
Hi community, I'm trying to get LibNXT working for Lego Mindstorms and that on Ubuntu 12.04 LTS.

According to the libnxt-0.3 README

> To compile all of this you'll need a copy of libusb 0.1 on your
system, as well as the scons project manager.

 - Libusb 0.1: [http://libusb.sf.net/](http://libusb.sf.net/)

Here's the output of ```
apt-file search -x 'libusb\.h$'
```

```
apcupsd-doc: /usr/share/doc/apcupsd/examples/libusb.h
libusb-1.0-0-dev: /usr/include/libusb-1.0/libusb.h
```

So I've installed the libusb that's available and scons. Here's where the problem appears:

> run 'scons' in the libnxt directory, and compilation should follow

Attempting that, the following happened:

```
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
gcc -o firmware.o -c -Wall -std=gnu99 -g -ggdb -D_NXT_LITTLE_ENDIAN firmware.c
In file included from firmware.c:31:0:
lowlevel.h:25:17: fatal error: usb.h: No such file or directory
compilation terminated.
scons: *** [firmware.o] Error 1
scons: building terminated because of errors.
```

In the hope that libusb.h would be a suitable substitute for usb.h, I did this

$ sudo cp /usr/include/libusb-1.0/libusb.h /usr/include/usb.h but this gave a screenful of error messages.

This issue (or similar) has been mentioned on
[http://code.google.com/p/libnxt/issues/detail?id=6]("This bug report")

Which recommends the following:

> change these two lines in SConstruct:

```
Default(BuildEnv.Program('fwflash', 'main_fwflash.c',
                         LIBS=['nxt', 'usb'], LIBPATH='.'))

Default(BuildEnv.Program('fwexec', 'main_fwexec.c',
                         LIBS=['nxt', 'usb'], LIBPATH='.'))

```

But having done that, the **usb.h** file is still missing.

Can anyone shed some light?

---


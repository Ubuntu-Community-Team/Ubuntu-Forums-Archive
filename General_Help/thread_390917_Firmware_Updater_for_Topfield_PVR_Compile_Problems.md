---
title: "Firmware Updater for Topfield PVR Compile Problems"
date: 2007-03-22
forum: General Help
---

### Post by gavinjb on 2007-03-22
Hi

I am trying to compile and install the topfield pvr firmware updater, but when ever i try I get the following error:

```

make tofu
if [ ! -d libtopfield ]; then ln -s ../libtopfield .; fi
make -C libtopfield
make[1]: Entering directory `/home/gavinjb/Desktop/tofu-0.1.0/libtopfield'
cc -Wall -Werror -D_FILE_OFFSET_BITS=64 -O2   -c -o tf_io.o tf_io.c
In file included from tf_io.c:26:
usb_io.h:37:23: error: linux/usb.h: No such file or directory
make[1]: *** [tf_io.o] Error 1
make[1]: Leaving directory `/home/gavinjb/Desktop/tofu-0.1.0/libtopfield'
make: *** [libs] Error 2

```

Can anyone help with getting this to compile.

---

### Post by fabertawe on 2007-03-22
I'm thinking of getting one of these PVRs and just compiled **ftpd-topfield** from [www.toppy.org](www.toppy.org) with a simple 'make'. Which software are you trying to compile? Let me know and I'll try it here. Maybe you have a missing USB dev library.

Paul

---

### Post by gavinjb on 2007-03-22
Hi I am trying to compile ToFu from [www.toppy.org.uk](www.toppy.org.uk)

For software for transferring files between the PVR and Linux I use Puppy (command line tool) and Guppy (GUI) and Guppy is far better than the Windows Version Alistair, if you want to have a look (cant do much without a box to connect to) go to [http://download.savannah.gnu.org/releases/guppy/](http://download.savannah.gnu.org/releases/guppy/)

Guppy requires Puppy to work.

---

### Post by fabertawe on 2007-03-22
> **gavinjb said:**
> Hi I am trying to compile ToFu

Thanks for the info. Ok, I just tried it and got the same error. I have all the USB dev libraries so it's not that.

Have you tried ftpd-topfield? That seems like an all in one solution and compiled easily. I'd be interested to know how you get on please as I do fancy one of these toppies.

Cheers ... Paul

---

### Post by fabertawe on 2007-03-22
It appears make is looking for usb.h in /usr/include/linux whereas it's in usr/src/linux-headers-2.6.17-10/include/linux

Making a link for it in /usr/include/linux and also for mod_devicetable.h gets me here...
```
paul@ubuntu:~/temp/tofu-0.5.1$ make
if [ ! -d libtopfield ]; then ln -s ../libtopfield .; fi
make -C libtopfield
make[1]: Entering directory `/home/paul/temp/tofu-0.5.1/libtopfield'
cc -Wall -Werror -D_FILE_OFFSET_BITS=64 -O2 -g   -c -o tf_io.o tf_io.c
In file included from /usr/include/linux/usb.h:4,
                 from usb_io.h:37,
                 from tf_io.c:26:
/usr/include/linux/mod_devicetable.h:21: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:36: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:119: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:143: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:157: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:162: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:189: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:222: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
/usr/include/linux/mod_devicetable.h:280: error: expected specifier-qualifier-list before ‘kernel_ulong_t’
make[1]: *** [tf_io.o] Error 1
make[1]: Leaving directory `/home/paul/temp/tofu-0.5.1/libtopfield'
make: *** [libs] Error 2

```

I'm afraid I'm stumped now! Hopefully someone knowledgeable will post.

Paul

---

### Post by gavinjb on 2007-03-23
Thanks for the help, just a thought do you think if I installed the Windows Firmware updated in Wine that it would work, I have tried installing and it installs and runs OK, but not sure if the firmware updater part will work (would it be able to connect to the device through usb?, and I cant try as I am running the latest firmware.

If it will it would be a much easier solution than trying to get this to work!


Gavin,

---

### Post by fabertawe on 2007-03-23
Hi Gavin,

I don't think Wine can access USB but only one way to find out!

I'm running XP through VMWare and that *can* access USB so if/when I get the PVR I'll test this out.

Paul

---

### Post by gavinjb on 2007-03-24
Paul,

Thanks for the info, as per your previous question I have not tried the ftpd-topfiled on Ubuntu, I tried it when I was using Suse and had no end of problems trying to get it to compile, so I went for the puppy/guppy solution instead, my understanding was that ftpd-topfield was an alternative to using guppy and only for transfering files to/from the toppy.

If you do get a toppy I would reconmend installing the mystuff tap as it really expands the usability of the box.

Gavin,

---


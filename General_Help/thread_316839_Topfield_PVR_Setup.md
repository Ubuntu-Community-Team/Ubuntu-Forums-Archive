---
title: "Topfield PVR Setup"
date: 2006-12-11
forum: General Help
---

### Post by gavinjb on 2006-12-11
Hi,

I found the How To on setting up a Topfield PVR with Ubuntu, but it doesnt mentioned anything about how to install Puppy/Guppy, can I do this through the repositories or do I need to download and compile the source, if I need to do the later has anyone had success as I have had major problems with trying to do this in the past.

The How To I found was
[http://ubuntuforums.org/showthread.php?t=307216](http://ubuntuforums.org/showthread.php?t=307216)


Thanks,


Gavin

---

### Post by georgie on 2006-12-11
Hiya

Funnily enough, I'm trying to do this now.

There are binaries here [http://download.savannah.gnu.org/releases/guppy/](http://download.savannah.gnu.org/releases/guppy/)

which work just fine on edgy x86.

I'm trying to compile ftpd-topfield and it's moaning about libusb

#usb_io.h:37:23: error: linux/usb.h: No such file or directory
make[1]: *** [tf_io.o] Error 1


I have libusb-dev and usbutils installed along with various linux-headers, etc.

Any thoughts?

George

---

### Post by gavinjb on 2006-12-11
Hi,

I had a similar problem when trying to install it on Mandriva 2007, (it complained about BITS_PER_LONG /usr/include/linux/mod_devicetable.) let me know if you manage to get it working, and I will give it a try once I get my box up and running and see if it works for me.

the solution was to install PyGtk2.0-2.10.1, only problem was it gave other errors

---

### Post by gavinjb on 2006-12-12
Hi,

When I try to compile Puppy I get the following error, has anyone got any ideas, as after doing some googling, I am stuck

```

make
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o puppy.o puppy.c
In file included from puppy.c:48:
usb_io.h:33:23: error: linux/usb.h: No such file or directory
In file included from puppy.c:48:
usb_io.h:137: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
usb_io.h:137: warning: its scope is only this definition or declaration, which is probably not what you want
usb_io.h:139: warning: &#8216;struct usb_config_descriptor&#8217; declared inside parameter list
usb_io.h:141: warning: &#8216;struct usb_descriptor_header&#8217; declared inside parameter list
usb_io.h:143: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
usb_io.h:144: warning: &#8216;struct usb_config_descriptor&#8217; declared inside parameter list
puppy.c:69: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
puppy.c: In function &#8216;main&#8217;:
puppy.c:98: error: storage size of &#8216;devDesc&#8217; isn&#8217;t known
puppy.c:98: warning: unused variable &#8216;devDesc&#8217;
puppy.c: At top level:
puppy.c:1138: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
puppy.c:1139: error: conflicting types for &#8216;isToppy&#8217;
puppy.c:69: error: previous declaration of &#8216;isToppy&#8217; was here
puppy.c: In function &#8216;isToppy&#8217;:
puppy.c:1140: error: dereferencing pointer to incomplete type
puppy.c:1140: error: dereferencing pointer to incomplete type
make: *** [puppy.o] Error 1

```

Thanks,

---


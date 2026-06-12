---
title: "Compiling error with Realtek audio driver."
date: 2014-08-04
forum: General Help
---

### Post by %cV4BU£r8Ofp&amp;# on 2014-08-04
Im trying to install realtek driver in my Ubuntu 14.04.1 LTS. I follow their installation guide. First i run (all with root) ./configure and everything works fine. After that i run make and i get this error:
```

/home/~~/alsa-driver-RTv5.18/alsa/usb/misc/ua101.c: In function ‘ua101_disconnect’:
/home/~~/alsa-driver-RTv5.18/alsa/usb/misc/ua101.c:1357:2: error: implicit declaration of function ‘__list_for_each’ [-Werror=implicit-function-declaration]
  __list_for_each(midi, &ua->midi_list)
  ^
/home/~~/alsa-driver-RTv5.18/alsa/usb/misc/ua101.c:1358:3: error: expected ‘;’ before ‘snd_usbmidi_disconnect’
   snd_usbmidi_disconnect(midi);
   ^
cc1: some warnings being treated as errors
make[4]: *** [/home/~~/alsa-driver-RTv5.18/alsa/usb/misc/ua101.o] Error 1
make[3]: *** [/home/~~/alsa-driver-RTv5.18/alsa/usb/misc] Error 2
make[2]: *** [/home/~~/alsa-driver-RTv5.18/alsa/usb] Error 2
make[1]: *** [_module_/home/~~/alsa-driver-RTv5.18/alsa] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.13.0-32-generic»
make: *** [compile] Error 2

```

"se sale del directorio" means "leaving directory"

I've tried to continue the installation with make install but it doesnt work. I just get more errors. How i can solve this? I need Realtek driver because the actual driver doesn't work well.

---

### Post by Bucky Ball on 2014-08-04
*Thread moved to **General Help**.*

You might have more luck here. ***Installations & Upgrades ***is for installation and upgrading of the Ubuntu OS itself.

(I originally moved this to 'Networking'. Wrong. My mistake, sorry. ;))

---

### Post by %cV4BU£r8Ofp&amp;# on 2014-08-07
Thanks.
Anyway it seems nobody knows the answer. I'll set this thread to solved because i've found a file inside the installation package which says that these drivers are supported on pevious kernel versions (2.x) so maybe the problem is just the lack of an actualized driver.

---

### Post by combzrecord on 2014-12-21
OK you have to past the option "--with-cards=hda-intel" to the ./configure , 

like explain in this article : [http://askubuntu.com/questions/462655/lubuntu-14-04-no-soundcard-detected-hda-intel-realtek-alc880](http://askubuntu.com/questions/462655/lubuntu-14-04-no-soundcard-detected-hda-intel-realtek-alc880)

is that ?

---


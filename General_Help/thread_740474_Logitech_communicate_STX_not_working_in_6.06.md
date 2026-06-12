---
title: "Logitech communicate STX not working in 6.06"
date: 2008-03-30
forum: General Help
---

### Post by kryos on 2008-03-30
:Followed alll similar threads with no success.  Not detected with Ekiga, Camorama, or Skype.  Not sure whwre to go from here.

.~$ lsusb
Bus 005 Device 003: ID 043d:00c1 Lexmark International, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 003: ID 047d:105e Kensington
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:08d7 Logitech, Inc
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000

:~$ cat /proc/bus/usb/devices
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-51-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1f.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=08d7 Rev= 1.00
C:* #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 128 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 192 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 384 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 512 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 6 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS= 768 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 0 Alt= 7 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  16 Ivl=1ms
I:  If#= 2 Alt= 2 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  32 Ivl=1ms

---

### Post by linuxwizard on 2008-03-30
You need the spca5xx driver. Your cam is listed here > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > Get driver here > [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by kryos on 2008-03-31
Thanks for your assistance.  Now if you could direct me towards a good tutorial on installation it would be great.  I've read one relating to Breezy but did not have much luck.

---

### Post by linuxwizard on 2008-03-31
This should help > [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

---

### Post by kryos on 2008-04-01
While trying to get through that tutorial I get an error at make.as follows:

root@pop-desktop:/usr/src/gspcav1-20071224# ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
root@pop-desktop:/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make: *** /lib/modules/2.6.15-51-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
root@pop-desktop:/usr/src/gspcav1-20071224#

Stuck.

---

### Post by kryos on 2008-04-01
OK.  I got a little farther along.  Using GCC 4.0 as that is what is returned by dmesg.

root@pop-desktop:/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=gcc-4.0 modules
/usr/src/linux-headers-2.6.15-51-386/scripts/gcc-version.sh: line 11: gcc-4.0: command not found
/usr/src/linux-headers-2.6.15-51-386/scripts/gcc-version.sh: line 12: gcc-4.0: command not found
make[1]: gcc-4.0: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-51-386'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/bin/sh: gcc-4.0: command not found
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 127
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-51-386'
make: *** [default] Error 2
root@pop-desktop:/usr/src/gspcav1-20071224#

Thoughts?

---

### Post by kryos on 2008-04-01
Getting Closer.
Now I truly think I've gone as far as I should this late evening.  I nope for some final guidance to get me through!

root@pop-desktop:/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=gcc-4.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-51-386'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
  CC [M]  /usr/src/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /usr/src/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/gspcav1-20071224/gspca.mod.o
  LD [M]  /usr/src/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-51-386'
root@pop-desktop:/usr/src/gspcav1-20071224# modprobe -r spca5xx
root@pop-desktop:/usr/src/gspcav1-20071224# rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
root@pop-desktop:/usr/src/gspcav1-20071224# make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
root@pop-desktop:/usr/src/gspcav1-20071224# modprobe spca5xx
FATAL: Module spca5xx not found.
root@pop-desktop:/usr/src/gspcav1-20071224#

---

### Post by kryos on 2008-04-02
Almost there.
Idecided to try a couple of different applications. First, Ekiga: recognised the camera but gave the following

Error while opening video device Logitech QuickCam Communicate S

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Could not open the chosen channel

However, Camorama would display a decent image and most functions seemed to work.
Any help?.

---

### Post by linuxwizard on 2008-04-02
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by kryos on 2008-04-02
Got video on channel 0 but nos sound/mic.  Druid detects sound but the sliders snap back to 0 when released.

Now when I try Camorama it would not start.  But now, with Firefox open it does!

I guess I'll try Ekiga in an actual call to see what happens.  Still somewhat concerned with the previous error report though.

---


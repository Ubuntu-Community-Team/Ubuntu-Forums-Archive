---
title: "usbhid mousepoll doesn't work?"
date: 2006-07-14
forum: General Help
---

### Post by equilibrium on 2006-07-14
I can't seem to get the usbhid module to work at anything different than 10ms.

Things I've tried so far:

put:
options usbhid mousepoll=2
into /etc/modprobe.d/options

rmmod usbhid & modprobe usbhid mousepoll=2ms

echo 2 >  /sys/module/usbhid/parameters/mousepoll
(re-plugin mouse)

all of them seem to give the same results:

cat /sys/module/usbhid/parameters/mousepoll
2

and

cat /proc/bus/usb/devices

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1532 ProdID=0002 Rev= 1.00
S:  Manufacturer=Razer
S:  Product=Razer Diamondback Optical Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 **Ivl=10ms**

It works on the [old kernel method (re-compile module)](http://news.equk.co.uk/index.php?action=fullnews&showcomments=1&id=42) on my other ubuntu install. :???: :-k

---

### Post by equilibrium on 2006-07-14
I just downloaded and compiled a program called evhz and it seems to report the mouse as being 500hz (2ms) :-k 

./evhz
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 500 (average hz = 484)
event1: latest hz = 250 (average hz = 480)
event1: latest hz = 500 (average hz = 476)

very strange

---

### Post by Eazy© on 2006-08-21
Did you ever find a solution to this? I really need to have 500hz on my mouse because it makes it all so much smoother when playing UT2004.

As it is now I have to after I boot/reboot:
```
sudo kate /sys/module/usbhid/parameters/mousepoll
```
change the 0 to 2 unplug the mouse and then put it back again to get 500hz.

I have search this forums but noone seems to know how to enable this automaticly. Is there really noone that have a solution for this???

---

### Post by dugan on 2007-08-26
> **equilibrium said:**
> I just downloaded and compiled a program called evhz and it seems to report the mouse as being 500hz (2ms) :-k 

Could you please post the evhz program, if you still have it?

Every link download link I found for it is dead.

---

### Post by PotatoSalad on 2007-08-30
> **dugan said:**
> Could you please post the evhz program, if you still have it?

Every link download link I found for it is dead.
Just found it on archive.org: [http://web.archive.org/web/20060623094750/http://homepages.nildram.co.uk/~kial/evhz.c](http://web.archive.org/web/20060623094750/http://homepages.nildram.co.uk/~kial/evhz.c)

---

### Post by biovore on 2007-11-11
Yeah these seems to have changed on gusty

The evhz program above won't build.. needs a #include<string.h> at the top, then it builds. (maybe something to do with newer gcc or something)

for now, you just have to add the following to lines to /etc/rc.local
<code>
echo "2" > /sys/module/usbhid/parameters/mousepoll
rmmod usbhid
modprobe usbhid
</code>

1 -> 1000 Hz (dosn't work on some devices)
2 -> 500 Hz (Works on most logitech stuff)
3 -> 250 Hz

Works here anyway..  If usbhid is built into the kernel you can specify it on the kernel cmd args (in grub) by appending usbhid.mousepoll=2 to the kernel params

---


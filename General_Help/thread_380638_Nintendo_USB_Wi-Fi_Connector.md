---
title: "Nintendo USB Wi-Fi Connector?"
date: 2007-03-09
forum: General Help
---

### Post by White_Wolfman on 2007-03-09
I just bought the Nintendo USB Wi-Fi connector. The only problem is, I have Ubuntu, not Windows XP. Wikipedia said that it should be possible to run on Linux, thanks to shared Ralink chipsets.

So... is it actually possible, and if so, how? :confused:

I'm running Edgy 6.10.

---

### Post by teaker1s on 2007-03-10
plug it in then in terminal
```
lsusb
``` when you know the chipset model you can then go about finding a driver/ ndiswrapper and windows driver

---

### Post by Darles on 2007-03-12
Hi Wolfman.

The only link i have is for this site

[Here]("http://masscat.afraid.org/ninds/rt2570.php")

It contains a hacked version of the rt2570 driver. As of yet i haven't been able to get it to compile with the kernel I'm using 2.6.17 although like you i'm on edgy.

When you download it comes with instructions on how to install. I can get to the install stage but then i try to install and this is as far as i get...


```
david@david-desktop:~/Desktop/nin_rt2570-1.1.0-b2/Module$ make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/david/Desktop/nin_rt2570-1.1.0-b2/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  INSTALL /home/david/Desktop/nin_rt2570-1.1.0-b2/Module/nin_rt2570.ko
cp: cannot create regular file `/lib/modules/2.6.17-11-generic/extra/nin_rt2570.ko': Permission denied
make[2]: *** [/home/david/Desktop/nin_rt2570-1.1.0-b2/Module/nin_rt2570.ko] Error 1
make[1]: *** [_emodinst_] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [modules_install] Error 2
]
```

Am not quite sure what the problem is exactly as i'm newish to Ubuntu but the Nintendo connector is one of two reasons why i can't give up windows completely [the other being a damn sony mp3 player].

Anyway don't know if this helps but that's as far as i've got with it. 

Darles

---

### Post by teaker1s on 2007-03-12
make sure you have 
```
sudo apt-get install build-essential
```
plus you must
```
sudo make install
```

---

### Post by Darles on 2007-03-13
Thanks Teaker1s.

The driver seems to be installed and there is an option to set up a wireless connection in network setting.

Will it be straightforward setting up this wireless connection? Any help would be appreciated.

Darles

---

### Post by teaker1s on 2007-03-13
I'm not sure I understand what you are trying to do, are you trying to use as an access point for wii or wireless for pc?
if pc then install 
```
sudo apt-get install network-manager-gnome
```

if as access point this isn't exactly what you want but may help  you
[https://wiki.ubuntu.com/forum/hardware/UseWirelessLaptopAsAnInternetAccessPoint?highlight=%28wireless%29]("https://wiki.ubuntu.com/forum/hardware/UseWirelessLaptopAsAnInternetAccessPoint?highlight=%28wireless%29")

---

### Post by Darles on 2007-03-14
it's to try and install it as an access point for my wii and ds. 

i'll have a look at the link you posted and see how i go.

---

### Post by brodiepearce on 2007-06-08
[Someone](http://archive.openbsd.nu/?ml=openbsd-misc&a=2006-04&m=1983405) has succeeded in getting this to function with OpenBSD-3.9b using the ural driver.  It's not much, but might help getting it to work on Ubuntu.

*edit*
As linked to in [this thread](http://ubuntuforums.org/showthread.php?t=391920), there is also a [hacked RT2570 driver](http://masscat.afraid.org/ninds/rt2570.php) available for it.  I'm looking at buying one of these in the future, as DS' only supports WEP encryption, an easier option would be to just use it on one of the windows PCs here...

---

### Post by Stokky on 2007-06-13
Anyone, any luck?

I'm also struggling to get a Nintendo Wi-Fi USB Connector going, but so far I didn't even manage to get the dongle's led to flicker like it does in Windows. I visited some of the links posted here and in other topics, but so far they didn't help much. If anyone finds new data on this topic, please let the rest of us know here...

---

### Post by brodiepearce on 2007-06-15
In my opinion it's definitely possible, hell some of the links prove that.  All it takes is a hacked driver or something similar really....

I can't comment much though, I haven't even bought one yet, guess it's better to map out a definite way of getting it to work on Ubuntu before I buy! ;)

---


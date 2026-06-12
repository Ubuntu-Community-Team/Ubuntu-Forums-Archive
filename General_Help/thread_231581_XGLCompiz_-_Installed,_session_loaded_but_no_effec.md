---
title: "XGL/Compiz - Installed, session loaded but no effects"
date: 2006-08-07
forum: General Help
---

### Post by chaosgeisterchen on 2006-08-07
Hi there,

I followed the HowTo on compiz.net [[click here]](http://www.compiz.net/viewtopic.php?id=389), well, better the identical HowTo on the UbuntuUser.de-Wiki, and everything seemed to work properly, freshly built binary ATI-Drivers and installed XGL/Compiz, Session loads well, but then: no effects at all :/

Anyone has a idea how I can be helped?

Thank you very much in advance,

some quite desperate

cg

---

### Post by Anduu on 2006-08-07
I used the excact same how to and XGL works flawelessly.

Are you sure your video drivers are installed correctly...does typing fglrxinfo in a terminal give something like this?

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

The only difference with my setup is I am using the xorg-driver-fglrx from the repos...ATIs driver has caused me nothing but trouble...

---

### Post by gorded on 2006-08-07
log out and go to options  session chooser and make sure Xgl is selected. Probably not whats wrong but give it a shot and make sure when loading the background is small black and white checkered square.

---

### Post by chaosgeisterchen on 2006-08-08
I already checked both, I can assure you, it becomes checkered black/grey, the background 'fades' but after that XGL seems to kill itself :/

@driver:

I will propably try it again with the official drivers. Anyone else any other suggestion upon this topic?

---

### Post by ARSCHKOCH on 2006-08-11
Hi,

i have used more or less the same howto in german with my ATI mobility Radeon X1600 and it seems like i have the same problem. I don't think Xgl is killing itself, because it's running in my case, which i checked with ps ax. 
Also i checked that in gconf-editor all plugins are activated like a gentoo Xgl troubleshooting guide suggested.
I use the latest fglrx driver from ATI.com, version 8.27.10 and it works, and here is the output of fglrxinfo:

muck@muck-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5946 (8.27.10)

could it be a problem, that my Xgl is running on another DISPLAY? I don't think so, but you never know...
muck@muck-laptop:~$ echo $DISPLAY
:1.0

the only strange thing in my Xorg.0.log is:
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card232
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

but i don't think these messages mean too much :/

Another thing is, that when i start ATI Control under a normal Session it works perfectly and shows the correct driver an kernel module, but when i start it in Xgl, before starting i get a error window saying "Driver does not provide the FireGL X11 extensions! Panel components will operate only partially."
Then it shows only the "Information" Pane with the correct OpenGL driver, but no normal 2d driver as it seems...

I hope somebody can help me with this... are there any logfiles that could be usefull? I uploaded my xorg.conf as a .txt and my Xorg.0.log as a gzipt txt...

Thank you for your help in advance,

best wishes,
Muck

---

### Post by Hickeroar on 2006-08-12
I've actually got a problem IDENTICAL to this one.  Any help would be greatly appreciated...

---

### Post by Tek12 on 2006-08-13
I went through MANY installations of Ubuntu to get this right.

I found that installing the ATI Proprietary drivers by building the debian packages manually, it would work when I went to install xgl/compiz.

So basically, I followed this first:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)

then I followed this (2nd method):

[http://www.compiz.net/topic-389-compiz-gnome](http://www.compiz.net/topic-389-compiz-gnome)

ATI Radeon 9800XT/8.27.10 drivers/Ubuntu 6.06.1/gnome/fglrx/xgl/compiz

Good luck!

---


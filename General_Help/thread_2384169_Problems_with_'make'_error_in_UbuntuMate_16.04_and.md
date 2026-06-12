---
title: "Problems with 'make' error in UbuntuMate 16.04 and Raspberry pi 3"
date: 2018-02-03
forum: General Help
---

### Post by calabuig1969 on 2018-02-03
Hello, I'm trying to make my m2tech Hiface Evo work under UbuntuMate 16.04 and Raspberry pi 3.
The interface works very well under ArchLInux, but in Ubuntu there's no USB-SND-HIFACE.KO module.
So I tried to follow a guide with this instructions:

```
sudo apt install build-essential
sudo apt install git
git clone [https://github.com/panicking/snd-usb-asyncaudio.git](https://github.com/panicking/snd-usb-asyncaudio.git)
cd snd-usb-asyncaudio
make
sudo insmod snd-usb-hiface.ko
```
But when I givre the 'make' command I receive this error:
```

make -C /lib/modules/4.9.79-v7+/build SUBDIRS=/home/calabuig/snd-usb-asyncaudio modules
make[1]: *** /lib/modules/4.9.79-v7+/build: No such file or directory. Stop.
Makefile:8: recipe for target 'default' failed
make: *** [default] Error 2
```

Is there anyone who could help me?
Thanks in advance!

---

### Post by steeldriver on 2018-02-03
The message 

```

make[1]: *** /lib/modules/4.9.79-v7+/build: No such file or directory. Stop.

```

is probably telling you that your system doesn't have the kernel headers installed

However, the project's README.md file says that:

> 
This driver is available in mainline linux since v3.11 under sound/usb/hiface/

Make sure to enable SND_USB_HIFACE to have it built.

This out-of-tree driver is just to keep an history of the development and
for poeple using kernels older than 3.11


so I doubt it is going to do any good on your system (which I assume is running a 4.x.x kernel).

---

### Post by calabuig1969 on 2018-02-03
I tried with the script here:

[https://github.com/gilesw/volumio-customizations/](https://github.com/gilesw/volumio-customizations/)

but I receive the same error.
The strange thing is that the needed module (usb.snd-hiface.ko) is present under ArchLinux distribution so it should be possible to make it work under Ubuntu, too.

---

### Post by jeremy31 on 2018-02-03
The module is present on my Ubuntu 16.04 install, try ```
locate snd-usb-hiface.ko
```

The panicking github appears to be for kernels older than 3.11

---

### Post by steeldriver on 2018-02-03
It's available as well in regular Ubuntu kernels e.g. on my 16.04 x86_64 VM:

```

$ modinfo snd-usb-hiface
filename:       /lib/modules/4.4.0-112-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
license:        GPL v2
description:    M2Tech hiFace USB-SPDIF audio driver
author:         Antonio Ospite <ao2@amarulasolutions.com>
author:         Michael Trimarchi <michael@amarulasolutions.com>
srcversion:     594C08E94CCDCC724AA092A
alias:          usb:v25C6p9002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v245Fp931Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp932Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp931Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp9008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp9006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp9002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v249Cp9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p9321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p9320d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p931Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p931Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p931Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p931Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p931Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p930Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B4p0384d*dc*dsc*dp*ic*isc*ip*in*
depends:        snd-pcm,snd
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions
parm:           index:Index value for hiFace soundcard. (array of int)
parm:           id:ID string for hiFace soundcard. (array of charp)
parm:           enable:Enable hiFace soundcard. (array of bool)

```

I don't know anything about the Raspberry Pi / ARM kernels but for whatever reason yours seems to be configured without it

---

### Post by calabuig1969 on 2018-02-03
I can't find it.
Could you send me your module?
Do you think I can install yours?
Or how can I compile it?

---

### Post by steeldriver on 2018-02-03
You will need a kernel built for your target (ARM) architecture that has been configured to build the appropriate module(s) - that's beyond my expertise unfortunately

[https://sysprogs.com/VisualKernel/tutorials/raspberry/buildkernel/](https://sysprogs.com/VisualKernel/tutorials/raspberry/buildkernel/)

You might have more luck asking on a dedicated pi forum

---


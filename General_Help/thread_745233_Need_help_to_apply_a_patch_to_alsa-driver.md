---
title: "Need help to apply a patch to alsa-driver"
date: 2008-04-04
forum: General Help
---

### Post by bofphile on 2008-04-04
Hi,

I'm trying to make work my external soundcard (E-Mu 0202 USB), and apparently I need to apply a patch to alsa-driver for doing so. I've followed this thread: [http://ubuntuforums.org/showthread.php?t=441946&highlight=0404&page=13]("http://ubuntuforums.org/showthread.php?t=441946&highlight=0404&page=13") and downloaded the patch "usbaudio.c" but I have no idea how to apply it.

For now this is what I did:```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
cd /usr/src
sudo tar xjvf alsa-driver.tar.bz2
cd /modules/alsa-driver
```

and now before compiling I need to know the command line to apply the patch.

Thanks.

---

### Post by geraldm on 2008-04-04
A proper patch is a difference file, usually ending in ".diff" in its filename.
To apply it, you are to be in the top directory of the source, or sometimes the directory immediately above the top source directory, and use
patch -p0 -i ../patch.diff
the "-p0" is a strip option, and you need the correct number for the patch.  0 or 1 usually work.

You have a filename of usbaudio.c and it probably is NOT a patch difference file.

Gerald

---

### Post by bofphile on 2008-04-04
Thanks geraldm for the explanation. This is where I got the file:
**[http://hg.alsa-project.org/alsa-kernel/rev/247195dfda43]("http://hg.alsa-project.org/alsa-kernel/rev/247195dfda43")**

Do you have any idea how I could use the file, as some have done apparently:
> **luarvik said:**
> Thank you so much!!

I just applied the patch you posted on alsa-devel and my sync issues are gone and the card works flawlessly. The sound is perfect!

Once again, thank you.

> **billstei said:**
> Just for kicks I tried applying the patch to the stock Ubuntu Gutsy 1.0.14 alsa-driver source and it patches (and compiles) fine.  I am guessing that the only file that really needs to be installed is "snd-usb-audio.ko" which is located at:

/lib/modules/2.6.22-14-whatever_your_kernel_is_named/kernel/sound/usb/snd-usb-audio.ko

and is normally a part of the linux-image-2.6.22-xxxxxxx package.  Seems like the least intrusive way to do this would be to just copy over the ko file.  Yes, no?

Bill


I've already tried to contact them with no success.

Thanks a lot.

---


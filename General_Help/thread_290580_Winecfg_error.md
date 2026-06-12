---
title: "Winecfg error"
date: 2006-11-01
forum: General Help
---

### Post by bolt212 on 2006-11-01
when i click on the audio tab i get this printed in the console.

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c040bb8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

and winecfg freezes up and i have to terminate it to close it.

---

### Post by bolt212 on 2006-11-01
as a side note,   main reason for using wine is to run Ventrilo.

I can't get vent to work with cedega and WoW at the same time,  so i'm trying to run WoW in cedega and Vent in wine to see if that will help.

---

### Post by bolt212 on 2006-11-01
bump from page 7 after 6 hours O.o

---

### Post by bolt212 on 2006-11-01
anyone?

---

### Post by machoo02 on 2006-11-01
what version of wine are you using?

---

### Post by tajmox on 2006-11-02
Solved! Try This:

```
sudo mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts
```

Audio Tab works when I do that.
You might get more errors but you can ignore them.
Sound works when "Emulation" is on

---

### Post by karhulitos on 2006-11-04
Thanks, that worked for me. However the sound I hear is poor quality. It kinda cuts the sound all the time.. Any ideas?

---

### Post by the-linux-guy on 2006-11-04
Use "jack" and "alsa" as your sound-drivers in Wine...
Jack needs libjack.so, so install it through apt-get with
```

sudo apt-get install libjack0.100.0-0

```

---

### Post by karhulitos on 2006-11-07
> **the-linux-guy said:**
> Use "jack" and "alsa" as your sound-drivers in Wine...
Jack needs libjack.so, so install it through apt-get with
```

sudo apt-get install libjack0.100.0-0

```

OK tried that but it said to me:
```
libjack0.100.0-0 on jo uusin versio. (sorry, finnish. Says it's already most recent version)
```

But winecfg says to me when I click sound tab:
```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

?? Well, actually I'm not needing sound that much in wine but if someone knows how to get it running, I wo't complain!

cheers,
Timo

---


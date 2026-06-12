---
title: "No soundcard detected"
date: 2013-03-24
forum: General Help
---

### Post by agzt on 2013-03-24
Hello again community, it has been a while after my first post in November 1st, 2011 about my problem with the soundcard (that I haven't solved it yet, I gave up.), now I'm back because I need it to work...

(old thread: [http://ubuntuforums.org/showthread.php?t=1873145](http://ubuntuforums.org/showthread.php?t=1873145))

I made this new thread to be more "cleaner", I will put all the info I have.

Now I have ubuntu 12.10 32 bits, my soundcard is onboard (Realtek ALC883 @ VIA VT8237A High Definition Audio Controller)

***uname -a***
```
Linux agzt29pc 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:20:06 UTC 2013 i686 athlon i686 GNU/Linux
```

***aplay -l***
```
aplay: device_list:252: no soundcards found...
```

***sudo lspci -v***
```
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
    Subsystem: Foxconn International, Inc. Device 0cf4
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fd00000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```


***cat /proc/asound/version***
```
Advanced Linux Sound Architecture Driver Version 1.0.25.
```

***cat /proc/asound/cards***
```
--- no soundcards ---
```

***sudo modprobe snd-***
```
FATAL: Module snd_ not found.
```

Here is the alsa-info
> [http://www.alsa-project.org/db/?f=00efb592646288ca4b129e970b4e8f5919a1de23](http://www.alsa-project.org/db/?f=00efb592646288ca4b129e970b4e8f5919a1de23)

---

### Post by agzt on 2013-03-25
bump

---

### Post by ManamiVixen on 2013-03-25
VIA Chipsets have **** poor support. Sorry, but it won't work unless you can compile your own drivers. VIA provides the source, but there are no instructions on how to do it.

---

### Post by agzt on 2013-03-26
> **ManamiVixen said:**
> VIA Chipsets have **** poor support. Sorry, but it won't work unless you can compile your own drivers. VIA provides the source, but there are no instructions on how to do it.

Dam >.<

no one with this chipset have sound on linux? :S

any one has got the link to the source code?

---

### Post by gordintoronto on 2013-03-26
Several years ago I bought a PCI sound card from Hong Kong for $5 (through eBay), and it worked like a champ. If this is a desktop computer, that might simplify your life.

If you're not sure about the innards of your computer, run:
sudo lshw -html > Desktop/config.htm

Double-click on the file, and it should identify your motherboard. I have always been able to find a motherboard manual on the Internet, although there have been times it took half an hour on Google.

---

### Post by agzt on 2013-03-27
> **gordintoronto said:**
> Several years ago I bought a PCI sound card from Hong Kong for $5 (through eBay), and it worked like a champ. If this is a desktop computer, that might simplify your life.

If you're not sure about the innards of your computer, run:
sudo lshw -html > Desktop/config.htm

Double-click on the file, and it should identify your motherboard. I have always been able to find a motherboard manual on the Internet, although there have been times it took half an hour on Google.

Thanks... but for now I don't plan to buy one.

---

### Post by agzt on 2013-04-02
UPDATE: Running Ubuntu 12.10 in a virtual machine from windows, I have sound.

---


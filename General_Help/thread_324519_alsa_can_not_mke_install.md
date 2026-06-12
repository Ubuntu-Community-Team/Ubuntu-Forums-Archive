---
title: "alsa can not mke install"
date: 2006-12-23
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-23
I have compile the kernel 2.6.19.1,with the help of others,I success.
Now there is no sound in the new kernel,when I opened a mp3 file,It showed that :
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
So I download 
alsa-driver-1.0.8.tar.bz2
alsa-lib-1.0.8.tar.bz2
alsa-utils-1.0.8.tar.bz2
then
tar -xvfj alsa-driver-1.0.8.tar.bz2
tar -xvfj alsa-lib-1.0.8.tar.bz2
tar -xvfj alsa-utils-1.0.8.tar.bz2
then
cd alsa-driver-1.0.13 && ./configure && make 
not successful ,the error showed:
make[1]: *** [hwdep.o] Error 2
make[1]: Leaving directory `/home/lotus/alsa-driver-1.0.8/acore'
make: *** [compile] Error 1
and  make install error is:
make[2]: *** [conf.lo] Error 1
make[2]: Leaving directory `/home/lotus/alsa-lib-1.0.8/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/lotus/alsa-lib-1.0.8/src'
make: *** [install-recursive] Error 1
If I do the same thing to alsa-lib-1.0.8.tar.bz2
then make alsa-utils-1.0.8.tar.bz2 ,it show:
make: *** No targets specified and no makefile found.  Stop.

I have no idea about that.

---

### Post by pay on 2006-12-23
You need to compile the kernel with these options```
Device Drivers  --->
    Character devices --->
        <*> Enhanced Real Time Clock Support
    Sound  --->
        <M> Sound card Support
            Advanced Linux Sound Architecture  --->
                <M> Advanced Linux Sound Architecture
                <M> Sequencer Support
                <M> OSS Mixer API
                <M> OSS PCM (digital audio) API
                <M> RTC Timer support
                < > Verbose printk
                < > Debug
                Generic Devices  --->
                PCI Devices  --->
                USB Devices  --->
            Open Sound System  --->
                < > Open Sound System (DEPRECATED)
```

---

### Post by LaoLiulaoliu on 2006-12-23
can you give more details about follows:
                Generic Devices  --->
                PCI Devices  --->
                USB Devices  --->
            Open Sound System  --->
                < > Open Sound System (DEPRECATED)
I can not find this option in google or other forum.

---

### Post by pay on 2006-12-23
Go to device drivers --> sound --> open sound system

---

### Post by LaoLiulaoliu on 2006-12-24
I am so sure that I have done what you say what I should do.
So may be you are wrong

---

### Post by pay on 2006-12-24
Well it is right because I've compilled alot of kernels and gotten alsa to work, but if you don't want to believe the person that was trying to help you then you don't have to. Don't ask the questions if you don't want the answers.

---

### Post by LaoLiulaoliu on 2006-12-24
I am sorry.

---

### Post by pay on 2006-12-24
I didn't mean to seem angry. It was just late at night. Anyway I found some more descriptive kernel options for you. The difference between compilling the kernel with alsa support and building the alsa package is that the kernel support is easier to mantain when you compile new kernel's frequently.```
Device Drivers  --->
   Sound  --->
   
(This needs to be enabled)
<M> Sound card support

(Make sure OSS is disabled)
Open Sound System   --->
   < > Open Sound System (DEPRECATED)

(Move one step back and enter ALSA)
Advanced Linux Sound Architecture  --->
   <M> Advanced Linux Sound Architecture
   (Select this if you want MIDI sequencing and routing)
   <M> Sequencer support
   (Old style /dev/mixer* and /dev/dsp* support. Recommended.)
   <M> OSS Mixer API
   <M> OSS PCM (digital audio) API 

(You now have a choice of devices to enable support for. Generally,
you will have one type of device and not more. If you have more than one 
sound card, please enable them all here.)

(Mostly for testing and development purposes, not needed for normal 
users unless you know what you are doing.)
Generic devices  --->
   
(For ISA Sound cards)
ISA devices   --->
(IF you had the Gravis, you would select this option)
   <M> Gravis UltraSound Extreme

(Move one level back and into PCI devices. Most sound cards today are 
PCI devices)
PCI devices   --->
   (We now select the emu10k1 driver for our card)
   <M> Emu10k1 (SB Live!, Audigy, E-mu APS)
   (Or an Intel card would be)
   <M> Intel/SiS/nVidia/AMD/ALi AC97 Controller
   (Or if you have a VIA Card)
   <M> VIA 82C686A/B, 8233/8235 AC97 Controller

(Move one level back and select in case you have an USB sound card)
USB Devices   --->
```They are the options you need to build the kernel with. If your kernel wasn't built with those options then you will need to completly recompile the kernel. Once that's done and it still doesn't work try invoking alsaconf```
sudo alsaconf
```i assume it is installed with Ubuntu at default.```
/etc/init.d/alsasound start
```which should then result in something like this```
 * Loading ALSA modules ...
 * Restoring Mixer Levels ...     [ ok ]
```Then use alsa mixer and make sure that all the channels are unmutted```
sudo alsamixer
```Goodluck.

---

### Post by LaoLiulaoliu on 2006-12-25
I have recompiled my kernel,the sound come.
But the new problem is the "stardict" don't phonate.and bash can not find the commond "sudo alsaconf"
And another problem come :when I insert cd-rom and try to open it ,pop a message box:
Couldn't display "cdda:///dev/scd0"
There was an error launching the application.
**Merry Christmas!**

---

### Post by LaoLiulaoliu on 2006-12-25
My PCI drives is  nVidia Corporation,my motherboard is nvidia Gforce 6100

---

### Post by LaoLiulaoliu on 2006-12-25
My PCI drives is  nVidia Corporation,my motherboard is nvidia Gforce 6100
amd64 cup

---

### Post by pay on 2006-12-25
> **LaoLiulaoliu said:**
> I have compile the kernel 2.6.19.1,with the help of others,I success.
Now there is no sound in the new kernel,when I opened a mp3 file,It showed that :
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

Oh god I'm such an idiot. I just skipped though and saw that you compilled your own kernel and were trying to compile alsa and didn't see that line and assumed the problem was alsa. The problem is not your kernel or alsa but it's probably because you don't have the codecs installed properly. Have a look at this [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
Sorry for screwing you around and wasting your time. Merry Christmas, or happy holidays depending on your beliefs:)

---

### Post by LaoLiulaoliu on 2006-12-26
anyhow ,thank you!
We can discuss more .

---


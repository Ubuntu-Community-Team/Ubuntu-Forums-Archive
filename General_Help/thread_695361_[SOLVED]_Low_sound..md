---
title: "[SOLVED] Low sound."
date: 2008-02-12
forum: General Help
---

### Post by solarwind on 2008-02-12
Problem: low sound, even when all the dials on alsamixer are turned up to the max.
Hardware: Gigabyte ga-ma69vm-s2 motherboard with integrated sound (Realtek ALC888 Audio Codec)
**Fixed. I created a tutorial to fix this: [http://www.blog.solarwind.metafy.org/2008/02/17/fixing-alc888-sound-problems-on-ubuntu-710/](http://www.blog.solarwind.metafy.org/2008/02/17/fixing-alc888-sound-problems-on-ubuntu-710/)**

---

### Post by solarwind on 2008-02-13
Bump...

---

### Post by solarwind on 2008-02-13
Bump.

---

### Post by alejo0823 on 2008-02-17
I have that exact audio (ALC 888) and its also very low, the volume its audible but I would like a solution. it really disappoints when you wana hear a song very loud but its already 100%.

---

### Post by solarwind on 2008-02-17
> **alejo0823 said:**
> I have that exact audio (ALC 888) and its also very low, the volume its audible but I would like a solution. it really disappoints when you wana hear a song very loud but its already 100%.

I fixed mine. Give me a day or two and I'll post a howto. It's sad that no one bothered to even help with this so I never bothered to reply or mark as solved, but since you need help, I'll post a howto.

---

### Post by Sokertes on 2008-02-17
On my laptop I have 

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller

and had the same problem you have.

I ended up fixing it with putting this in my grub on the kernel line

snd-hda-intel.position_fix=1

I know it is not the same card but it might help you get in the right direction for a fix

---

### Post by solarwind on 2008-02-17
Here's the solution, I wrote the tutorial: [http://www.blog.solarwind.metafy.org/2008/02/17/fixing-alc888-sound-problems-on-ubuntu-710/](http://www.blog.solarwind.metafy.org/2008/02/17/fixing-alc888-sound-problems-on-ubuntu-710/)

---

### Post by alejo0823 on 2008-02-17
hey thanks for helping I really think this is gona solve this, but I don't understand this step can you explain it pls

3. Compile and install the three packages in this order: alsa-driver, alsa-lib, alsa-utils. Use sudo for each of the configure, make and make install steps. A special note while compiling the alsa-driver package: configure it like this:

I don't know how to compile and don't know how to use the configure.
thanks.

---

### Post by solarwind on 2008-02-17
> **alejo0823 said:**
> hey thanks for helping I really think this is gona solve this, but I don't understand this step can you explain it pls

3. Compile and install the three packages in this order: alsa-driver, alsa-lib, alsa-utils. Use sudo for each of the configure, make and make install steps. A special note while compiling the alsa-driver package: configure it like this:

I don't know how to compile and don't know how to use the configure.
thanks.
I updated my blog post. I typed this howto while I was playing counterstrike and getting killed, so sorry for the poor quality. Also, I'm only 17, lol. If you don't understand, don't hesitate to post or email me.

---

### Post by alejo0823 on 2008-02-18
when I type
sudo ./configure –with-cards=hda-intel

I get

configure: error: invalid variable name: –with-cards

Im gona try continue without   –with-cards=hda-intel

---

### Post by FuturePilot on 2008-02-18
> **alejo0823 said:**
> when I type
sudo ./configure –with-cards=hda-intel

I get

configure: error: invalid variable name: –with-cards

Im gona try continue without   –with-cards=hda-intel

Try it with two "--"
```
--with-cards=hda-intel
```

---

### Post by solarwind on 2008-02-18
> **alejo0823 said:**
> when I type
sudo ./configure –with-cards=hda-intel

I get

configure: error: invalid variable name: –with-cards

Im gona try continue without   –with-cards=hda-intel

Two dashes in the front. If you continue without it, it wont work.

---

### Post by alejo0823 on 2008-02-18
hey thanks men it worked, the sound its a bit lower than with windows but its way better than before, and it fixed a problem with the master volume again thanks a lot.

---

### Post by solarwind on 2008-02-18
Anytime ;)

---

### Post by skankster on 2008-02-18
Nice one. Just been through the whole lot and it's sorted mine out, too.

---

### Post by nbayiha on 2008-03-07
I have the same problem with my sound , i tried to use OSS instead of Alsa but that didn't solve my problem , now i am going to tried ur how to , hoping it will sove my problem , anyway thanks that u did a How to it's surely going to help people around.
Thanks again.

I did tried it my sound problem is stil not as high as it is in vista.
Anyway thanks and by the way in ur last step when u said 
> sudo cp <alsa-driver's compile directory>/modules/* /lib/modules/2.6.22-14-generic/kernel/sound/
did u mean 
> sudo cp  /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
becase driver compile directory is the place where i did compile, and there is no module folder name module there buy when i tried the command above (i thougth i could have been that one u mean) the sound got back , buy with no increase.
Anyway like i already said thanks for u help.

---

### Post by solarwind on 2008-03-10
> **nbayiha said:**
> I have the same problem with my sound , i tried to use OSS instead of Alsa but that didn't solve my problem , now i am going to tried ur how to , hoping it will sove my problem , anyway thanks that u did a How to it's surely going to help people around.
Thanks again.

I did tried it my sound problem is stil not as high as it is in vista.
Anyway thanks and by the way in ur last step when u said 

did u mean 

becase driver compile directory is the place where i did compile, and there is no module folder name module there buy when i tried the command above (i thougth i could have been that one u mean) the sound got back , buy with no increase.
Anyway like i already said thanks for u help.

By the ALSA compile directory I meant the directory where *you* downloaded and compiled ALSA in.

Did you try anything? How did it go? Does it work/fail?

---

### Post by nbayiha on 2008-03-10
Actually it did work fine for me. 
Thanks.:)

---


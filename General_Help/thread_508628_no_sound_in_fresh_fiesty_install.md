---
title: "no sound in fresh fiesty install"
date: 2007-07-24
forum: General Help
---

### Post by roywhite on 2007-07-24
I've been using Ubuntu for about 2 years and i have a problem i never had before. I have no sound. my system is running a nf61s micro 754socket motherboard with an amd64bit  3200 processor. the onboard sound card is HDA Nvidia and the chip is a Realtek ALC861-VD. I have tried running alsamixer from terminal and the sound config tool from the menu. I can't get the sound to work at all. I dual boot with xp and the sound works perfectly in xp. my hard drive is a serial sata and I think that that may have something to do with it. The sound worked perfectly in vector, but it would freeze during boot sequence. Anyone have any suggestions besides RTFM which I have already done.    
roywhite

---

### Post by AceofSpades19 on 2007-07-24
why would your harddrive have anything to do with the sound?
You probably need drivers for your sound card, just go to google.com/linux and google drivers for it

---

### Post by longlegs on 2007-07-24
Hi ACE
The HDD and the Snd card may share interrupts and therefore interfere with each other.

Not to say that I believe this is or not the case here.

longlegs

---

### Post by AceofSpades19 on 2007-07-24
do you happen to know me from some other forum or something?

---

### Post by stchman on 2007-07-24
> **roywhite said:**
> I've been using Ubuntu for about 2 years and i have a problem i never had before. I have no sound. my system is running a nf61s micro 754socket motherboard with an amd64bit  3200 processor. the onboard sound card is HDA Nvidia and the chip is a Realtek ALC861-VD. I have tried running alsamixer from terminal and the sound config tool from the menu. I can't get the sound to work at all. I dual boot with xp and the sound works perfectly in xp. my hard drive is a serial sata and I think that that may have something to do with it. The sound worked perfectly in vector, but it would freeze during boot sequence. Anyone have any suggestions besides RTFM which I have already done.    
roywhite

Try this under the Toshiba HDA stuff.  It seems to work for HDA.

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

---

### Post by roywhite on 2007-07-24
Forget it, I'm going back to Vector
roywhite

---


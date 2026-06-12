---
title: "change color depth to 32 bit"
date: 2013-07-16
forum: General Help
---

### Post by deviderx on 2013-07-16
I have Ubuntu 13.04 amd 64 and I want to change color depth to 32 bit and i tried to change [COLOR=#000000]/etc/X11/xorg.conf but i think it didn't work 
please for help . [/COLOR]

---

### Post by CatKiller on 2013-07-16
Why is it that you think you need to do so?

32-bit isn't more betterer than 24-bit and 32-bit colour displays don't exist.

---

### Post by BreezyBrooke on 2013-07-16
What is your graphics card?

---

### Post by deviderx on 2013-07-16
I just want to know  
my card is intel G41

---

### Post by BreezyBrooke on 2013-07-16
Like CatKiller said, 32Bit color dosen't exist. All modern Video cards give 24bit+8bit. That 8bit on the end is for opacity and dosen't actually define color, just how transparent or solid it is. So under linux, we list 24bit color as a technicality. While Windows dosen't care and says "32bit". So 24bit is correct for your settings.

---


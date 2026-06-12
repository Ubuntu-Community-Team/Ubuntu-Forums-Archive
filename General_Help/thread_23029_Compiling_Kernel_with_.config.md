---
title: "Compiling Kernel with .config?"
date: 2005-03-30
forum: General Help
---

### Post by azuiden on 2005-03-30
Hello

recently i just switched to Linux and have seen the light and i am loving it

i installed MEPIS 3.3 but do the slowness decided to switch to Ubuntu (which i had installed before and liked but due to hardware issues could not get to work)

Well because i use a WUSB11 ver 2.6 USB (bloody atmel chipset) internet adapter (which i got to work on mepis) i need to compile the kernel source.

now in mepis there was a the handy the .config already in it and all i had to do was apply the patches and wait for 45 minutes and i had a compiled kernel

i was wondering (after poking around ubuntu for a bit) i was stumped to find that file, now the first time i compiled the kernel in MEPIS i did it without the .config file and i screwed it up and it took forever

does that file exist or do i have another option? i am currently running 4.10

---

### Post by mirtux on 2005-03-31
Hi,
  are you searching the .config file? Try with **locate .config **inside /usr/src.

Regards,
MC

---

### Post by az on 2005-03-31
Look in /boot for the config.

Install build-essential and linux-headers-(yourkernel)

---


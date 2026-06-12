---
title: "AVR Programming?"
date: 2007-07-16
forum: General Help
---

### Post by xelapond on 2007-07-16
I have BASCOM Sample Programmer for programming all my AVR projects.  Until recently I have been doing this on my pc, but my new linux box has both a paralell and serial port.  I found a program called KontrollerLab that looks like it will work, but when i try to comile a program it says:

avr-gcc -mmcu=at90s8515 -00 -c FlashLED.c -o FlashLED.o
Command not found: avr-gcc -mmcu=at90s8515 -00 -c FlashLED.c -o FlashLED.o
Error(s) occured: The exit status was 1.

What should I do to get it to program?  Or is there a better program to use?

Thanks, 

Alex

---

### Post by geraldm on 2007-07-16
There are many possible packages for the avr microcontroller series  under 
a wide variety of licenses.
avr-gcc appears to be from [http://www.nongnu.org/avr-libc/](http://www.nongnu.org/avr-libc/)
If you do not have the program installed, you can get it from that site.
You MAY also need the compiler tools, such as the build-essentials from ubuntu.

Gerald

---

### Post by xelapond on 2007-07-16
Thanks, I got it working...

---


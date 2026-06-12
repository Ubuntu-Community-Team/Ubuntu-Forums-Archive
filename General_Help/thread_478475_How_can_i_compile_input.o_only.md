---
title: "How can i compile input.o only?"
date: 2007-06-19
forum: General Help
---

### Post by Azathoth_ on 2007-06-19
I would like to compile /usr/include/linux/input.h  because i want to define a key KEY_STOP for example for a infrared remote control. I know the code (0x9e) but i need to define it. Also, i cannot add it to input.h, because it doesn't work

Thanks a lot

---

### Post by meatpan on 2007-06-19
Is there an application that requires KEY_STOP to be defined?  You should be getting compile errors in some c file if this is the case. 

In C, header files (files ending in '.h') aren't typically compiled by themselves.  Instead, various c programs will copy the information from appropriate header files directly into their source code.   This is why some people refer to header files as interfaces.  They present a common set of declarations to which multiple source files will comply.

Does this help?

---

### Post by Azathoth_ on 2007-06-19
> **meatpan said:**
> Is there an application that requires KEY_STOP to be defined?  You should be getting compile errors in some c file if this is the case. 

In C, header files (files ending in '.h') aren't typically compiled by themselves.  Instead, various c programs will copy the information from appropriate header files directly into their source code.   This is why some people refer to header files as interfaces.  They present a common set of declarations to which multiple source files will comply.

Does this help?

I know what is input.h and MOST C programs must include it and stdio.h  but in this file it is deffined the map keys, before xmodmap

I am using inputlirc to use lirc because i need this way and i want to define a key of my remote control. I cannot use xmodmap for this and, when i use xev i can see the code and the hexadecimal code of this key, but i don't know how to define it... and this is my question

Thnaks

---


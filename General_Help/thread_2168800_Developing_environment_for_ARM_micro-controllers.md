---
title: "Developing environment for ARM micro-controllers???"
date: 2013-08-19
forum: General Help
---

### Post by volter2 on 2013-08-19
Hello,

I'm looking for some nice UI for building projects for ARM micro-controllers core Cortex-M3/M4, simply the more supporting cores the better.
I'm familiar with Window's programs like Keil and IAR. Is there some toolkits for Eclipse or some other Linux compatible program to compile and flash programs into developing boards?
Is there some suggestions of how to make this work?

thank you,

---

### Post by davetv on 2013-08-19
If the board comes with a linux distro included, all you probably need to do to put data in flash is to ssh into it then scp files/programs etc.

I would use qt and associated tools to build with.

---

### Post by volter2 on 2013-08-19
Its not exactly what intended to. I seek for some program to be able to build projects in C/C++ for ARM Cortex M3/M4 and flash/download those compiled code to development boards, like LPC1679/1343, STM32F3 or STM32F4.
I don't want to manually compile each file in the terminal window.

---

### Post by davetv on 2013-08-19
You can develop/compile qt for ARM on your Linux desktop/laptop. The "target" is an ARM executable for a SBC/COM but the development and compiling is done on a bigger machine. You just transfer the target binaries to the SBC.

---


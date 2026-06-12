---
title: "shutdown problem"
date: 2013-05-19
forum: General Help
---

### Post by amiralex32 on 2013-05-19
dear all i have just upgrade from ubuntu 12.10 to 13.04 i faced a problem for shutdown when i shutdown the system a black screen appear has a message halt is going to execute then ubuntu screen appears and i stayed for 10 min and the computer never turn off thanks for help

---

### Post by oldschoolgentoo on 2013-05-19
What is your system?  aka  server, workstation, desktop or laptop to name a few.
what are you running as video, ram, processor?

Just a few items that might help others with your question about your system

on a side note have you looked over your  dmesg   output or kern.log?

---

### Post by amiralex32 on 2013-05-19
my system is a laptop memory 993.6 MiB processor Intel® Core&#8482; Duo CPU T2450 @ 2.00GHz × 2  graphics Intel® 945GM x86/MMX/SSE2 os 32-bit 
and i have not looked over [COLOR=#000000] dmesg output or kern.log (i don't know how ).
thanks for help[/COLOR]

---

### Post by oldschoolgentoo on 2013-05-19
From a terminal window  you can type

```
dmesg
```             # will output the file  
```
dmesg | less
```  # will  output in chunks as so you dont have to scroll the entire file from the last entry to the first.

from a terminal window the code above will shoot a large file onto the screen
pressing  q will exit the   less  pages and bring you back to a cursor

```
sudo nano -w /var/log/kern.log
```

use the arrow keys to scroll and move the mouse. 
press  ctrl-x  to exit the window and get back to  your_machine :~$

---

### Post by oldschoolgentoo on 2013-05-19
Now  dmesg is a as the system boots  log file as well if you add any  usb  or  say a cell phone or  other items to the system  it will give  you the name of the item 
```

[90932.357884] usb 1-8: New USB device found, idVendor=04e8, idProduct=6860
[90932.357890] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[90932.357893] usb 1-8: Product: Android
[90932.357896] usb 1-8: Manufacturer: Android
[90932.357899] usb 1-8: SerialNumber: 8w033fe8
```

Android cell phone listed above.  came from the  dmesg output


```
[    2.411574] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.411578] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.418032] Floppy drive(s): fd0 is 1.44M

```

as you can see from above  a network card and floppy drive.  It gives you alot of information  just learning  what you have and how to read the information.


its a very large file as well as the /var/log/kern.log

---

### Post by sudodus on 2013-05-19
> **amiralex32 said:**
> dear all i have just upgrade from ubuntu 12.10 to 13.04 i faced a problem for shutdown when i shutdown the system a black screen appear has a message halt is going to execute then ubuntu screen appears and i stayed for 10 min and the computer never turn off thanks for help

You can also have a look at the manual page of the command shutdown

```
 man shutdown
```

Notice the differences between the options

```
-h  either halt or power off
-H  halt
-P  power off
```

Now there are operating systems or versions that do not cooperate perfectly well will some hardware. Probably 13.04 does not power off your system, but it may still halt it. You can check that by pressing quickly (less than one second) the power button. If that will power off the computer, it is probably halted. Otherwise you would need something like 4 seconds for a hard poweroff, which is a bad idea, because the file system might get corrupted.

It is possible that you can make poweroff work with some boot option. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by claracc on 2013-05-19
> **amiralex32 said:**
> dear all i have just upgrade from ubuntu 12.10 to 13.04 i faced a problem for shutdown when i shutdown the system a black screen appear has a message halt is going to execute then ubuntu screen appears and i stayed for 10 min and the computer never turn off thanks for help

I think, this is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010981), you can help to fix it marking in the "this bug also affects me" link. 

I have a hp6720s compaq laptop and since ubuntu 12.04 was installed, it doesn`t shutdown when on battery ( remains in an infinite loop in the splash screen and don't halt) but it shutdown normally when on ac power. 

It haven't been fixed yet.

---

### Post by Ralph L on 2013-05-20
I was able to solve the shutdown problem on my Compaq Presarion 2100 by switching to Xubuntu 12.04.x  All the shutdown functions worked with Xubuntu right "out of the box".

---


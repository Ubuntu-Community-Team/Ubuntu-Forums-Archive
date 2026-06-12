---
title: "Older IBM, POST, GRUB, reboot, repeat"
date: 2007-05-17
forum: General Help
---

### Post by snazzed on 2007-05-17
1999 IBM Aptiva
AMD K6-2 500Mhz
192MB RAM
HD 10G
Kbd: US:international, PS2 / USB
Mouse: Logitech USB
Video: Voodoo 3 something or other
Ubuntu Server is the only install. No other OS

Was booting Win98 just fine. Wiped it, installed Ubuntu Server. POST ok, Grub lets me choose which Kernel to load, then very quickly flashes "Starting up" and then reboots.

Attempted Solutions:
   - Using a Live CD, and re-installing GRUB
   - replacing hard drives
   - Install XUbuntu instead
   - Use LiveCD, poke around the file system...  
      - couldn't find a grub.conf in /etc/ 
      - /initrd/ was empty?!

At this point I'm thinking, forget this ancient IBM (IBM did a lot of strange proprietary stuff) and find a slightly newer non-IBM.   Help?

Thanks
Snazzed

---

### Post by lorienp on 2007-05-17
I have an IBM Aptiva, AMD K6 3D Processor; 256 Mo RAM; RAGE PRO TURBO AGP . 
Obtained 'Xubuntu 6.10 "Edgy Eft" - Release i386 (20061025)' live disc.
After loading Kernel it declares 'Boot Error' and proposes reboot. I am a real beginner and cant get beyond this point.

---

### Post by snazzed on 2007-05-18
Ok, cruising around the web I've found a lot of people who can't boot Linux on Aptivas in this age range and I haven't found anyone with a good diagnosis or solution.

If anyone can help, please let me know.  If not I'll go looking for a new machine.

Thanks
     Snazzed

---

### Post by daschmidty on 2007-05-21
Here's how to fix it..it works on my k6-II 350MHZ.
Because the kernel is compiled for i686 or better, it freaks out on old hardware. Boot the alternate install cd and go into rescue mode. Execute a shell in the root of your install then:
```
apt-get install linux-386
apt-get remove linux-server
```


It can take awhile to generate the new boot image

---

### Post by cmcrgl on 2008-02-02
I have encountered the same problem with a K2- Aptiva.

I appreciate the information provided by daschmidty; however, daschmidty's proposes solution seems to imply a working installation that can be modified.  In my case, the machine reboots when attempting an initial install.  In attempting to use a recovery disk, the same thing happens, so I imagine that the kernel is too advanced there too for the hardware in this machine.

The ease of installation provided by Xubuntu's live disk seems to be something of a problem with old hardware.  If daschmidty is still monitoring this thread, I would appreciate a bit more detailed advice.

Currently, I seem to be successfully installing an old version of Corel Linux on this Aptiva.  It's kernel must be compatible with the hardware.

Would anyone know what the latest compatible version of Xubuntu would be?

Thanks for your help.

---

### Post by daschmidty on 2008-05-23
I'm back after a long hiatus, and not positve on this one, but if you want to stay current package-wise, you should be able to install debian etch with the netinstall cd, using a 386 kernel, and then update everything else to lenny(testing) using apt, but it may get a bit on the messy side. I am not really a kernel expert, I really only got that original solution through trial and error.

---

### Post by cmcrgl on 2008-05-23
Thank you for the suggestions.  In the interval since posting, I have found a different distro that seems better suited to this very old hardware, namely Damn Small Linux (DSL).  While I appreciate Ubuntu on more powerful hardware, DSL apparently uses a kernal that does not prompt the system restart.  As these machines will be used for web data entry, I don't need to much in the way of functionality beyond Firefox, so the spartan features of DSL are "good enough" for this particular application.

I do appreciate your answer, which may be of use to someone else who encounters this problem with older Aptivas, but who needs functionality beyond that provided by DSL.

Richard

---


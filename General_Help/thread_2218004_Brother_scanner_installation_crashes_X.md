---
title: "Brother scanner installation crashes X"
date: 2014-04-19
forum: General Help
---

### Post by horsemanoffaith-9 on 2014-04-19
I recently installed Ubuntu 14.04, and have been setting it up to work with my hardware and network attached devices. As I was doing so, I installed the drivers for my Brother MFC-J825DW multi-function machine. I used the Brother Linux printer installer script, which not only installed the drivers for my printer, but also for my scanner. Using xSane, my scanner is detected and is ready to be used for scanning. On my next restart, LightDM would not start and I was getting the low-resolution message. I dropped down to a command prompt and did a *startx *command- I discovered that my Catalyst drivers were crashing. The error had to do with /usr/lib64 file or directory not existing. After extensive troubleshooting, I found that the installation of my scanner drivers created the /usr/lib64 file, and Catalyst was searching for files inside of that directory, which it had not been doing before. I tried installing the 32-bit drivers to see if I could work around the /usr/lib64 problem, and the drivers did install, but for some reason I can't get xSane to detect my scanner, even though *brscan-skey -l* lists my scanner in its output. So, I can't install a working scanner driver without crashing X. Is this a bug that needs to be reported? If it is, who do I report the bug to... Ubuntu? AMD? Brother? Any advice would be appreciated.

---

### Post by Thomas_Grauschopf on 2014-05-19
I had the same problem with Ubuntu Precise (64 Bit, Radeon HD 8790M graphics card). After installation of drivers for Brother MFC 7360N (from official Brother download site; file was named linux-bprinter-installer-2.0.0-1.gz) and rebooting, the X server segfaulted. The first error message was

```
fglrx(0): PowerXpress: Cannot stat '/usr/lib64/fglrx': No such file or directory
```

/usr/lib64 only contained brother drivers for sane.

For me, renaming /usr/lib64 to /usr/lib64_bak solved the problem.

The bug should definitely be reported and fixed.

---

### Post by horsemanoffaith-9 on 2014-09-05
I tried what you posted, and that restores the functionality of my drivers for my video card, but xsane can no longer find the scanner. I searched for a way to link xsane/sane to the new directory, but I was unable to figure out how to do so. I'd like to get both my video drivers and scanner to work at the same time, if it's possible. I may have to post the problem to Brother or to AMD to see if they have any input on a resolution.

---

### Post by horsemanoffaith-9 on 2014-09-07
I fixed it! Now both my proprietary drivers and scanner work!!!! I used /var/log/Xorg.0.log to show me the errors, and I fixed them one by one. First of all, I copied the fglrx directory from lib32 into lib64. I then edited /usr/bin/fglrx/10fglrx to point to the /usr/lib64 directory. X still wouldn't start because it couldn't find switchlibGL. I copied switchlibGL and switchlibglx from /usr/lib/fglrx/ into the lib64 directory, and viola... X starts! There were still errors, however, and they pointed to directories that didn't exist. The errors stated they were both looking for fglrx_dri.so. I copied /usr/lib/dri (which contains that file) into /usr/lib64/dri, then created /usr/X11R6/lib64/modules/dri and copied fglrx_dri.so into it. X starts without the EE problems, but there is still one other thing I need to overcome: there is a system problem occuring every time I login. I'm not sure what the problem is, but I'll try to figure it out and report back here.

I know that creating symlinks would have probably been easier, but when I tried to figure out how to do so, I kept failing. I didn't want to screw the system up, so I just copied the file. I'll have to update this every time I update my video drivers more than likely, but at least I know how to fix it now!!!

---

### Post by horsemanoffaith-9 on 2014-09-07
It is now completely fixed. Did a system update and now there is no longer an error reported on login! Woo Hoo!!!

---


---
title: "compiz &amp; emerald in gutsy"
date: 2007-11-04
forum: General Help
---

### Post by Chymera on 2007-11-04
ok, so i just upgraded to gutsy and there's no way i can get my compiz fusion and the emerald engine to work...
i tried going to sys>prefs>appearance and enabling desktop effects...

It asks me if i want to enable the nvidia gfx accelerator, i click yes,then it tells me to restart, and then after booting i'm told that my monitor and gfx card are not recognized ...

I tried selecting them from the list, but neither are there.... so i choose whats closest, and voilà, cf still doesnt work.... 
and in addition i'm also stuck with some crappy display settings, only way to revert is sudo dpkg-reconfigure -phigh xserver-xorg ....
I had the nvidia 100.14.19 driver installed before upgrading, and now the settings manager just has one entry left.... no resolution, no refresh rate, no nothing, just some thing with tooltips...

I tried reinstalling the driver but it says it can't compile a kernel module because i don't have a kernel source.... strangely enough, one month ago the install of the driver went flawlessly on feisty...  

Any suggestions? I really need compiz, since i've gotten used to a lot of shortcut keys which don't work without it.... :(

---

### Post by Pumalite on 2007-11-04
sudo apt-get install linux-headers-`uname -r`

---

### Post by Chymera on 2007-11-04
what does that command do?

---

### Post by Pumalite on 2007-11-04
Installs the headers that you need according to your specific kernel.

---

### Post by Chymera on 2007-11-04
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.20-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.20-16-generic has no installation candidate
 Thats what i get :(

---

### Post by Pumalite on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=91999](http://ubuntuforums.org/showthread.php?t=91999)

---

### Post by Chymera on 2007-11-04
and what's that got to do with my problem?

---

### Post by Pumalite on 2007-11-04
I thought you might want to upgrade your kernel.

---

### Post by Chymera on 2007-11-04
i have a problem with the graphics driver, not the kernel...

---

### Post by Pumalite on 2007-11-04
'I tried reinstalling the driver but it says it can't compile a kernel module because i don't have a kernel source.... strangely enough, one month ago the install of the driver went flawlessly on feisty...'

If you want to install a new driver, you need the kernel-headers, and according to what we've been discussing, there are no headers for your kernel.

---

### Post by Chymera on 2007-11-04
hmmm... did they just get deleted in the "upgrade" ? 
I didn't think of it as a kernel problem since the kernel seems to work, it's the driver, or rather the way it is handled, which seems faulty....

But if you say it can be solved through getting some proper headings, i'll go with it... how do i get them.... I couldn't really make much out of those links :confused:

---


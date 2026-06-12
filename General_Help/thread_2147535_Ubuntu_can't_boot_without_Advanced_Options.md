---
title: "Ubuntu can't boot without Advanced Options"
date: 2013-05-22
forum: General Help
---

### Post by ocli5568 on 2013-05-22
Hello,

I was fiddling around with my graphics card drivers, and (believe) I successfully installed the ATI catalyst driver, however now I'm getting some strange boot issues.

When trying to boot normally (I dual boot) with grub: firstly, the grub screen is blue, not purple; and second, when trying to boot Ubuntu the screen blue's out and hangs indefinitely. I tried going into Advanced Options and found that when I used the 'dpkg' option (fix broken packages) a bunch of packages could not be fetched, and nothing was modified, yet exiting out of this mode and clicking the 'resume' option enables me to boot successfuly, however with a mirrored display only allowed for my dual monitors. It's safe to assume this is something I did wrong with the graphics driver but I don't really know where to go from here.

testing whether catalyst works:

```

$fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series 
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104

```
I'm running Ubuntu 13.04 with an Advanced Micro Devices [AMD] nee ATI Cape Verde PRO [Radeon HD 7750] controller.

Thanks for any help.

---

### Post by dino99 on 2013-05-22
from synaptic (install it if needed : sudo apt-get install synaptic  && sudo synaptic):
- check that : the linux kernel headers, built-essential are installed
- purge (right click the package) then reinstall the graphic driver  [http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

then logout & reboot

---

### Post by HiImTye on 2013-05-22
do:
```
sudo apt-get update; sudo apt-get install -y linux-headers-generic
```
then reinstall your graphics drivers:
```
sudo apt-get purge <packages>; sudo apt-get install <packages>
```

edit: if you're unsure what driver you're using, use:
```
sudo apt-get install aptitude; aptitude search fglrx~i
```

---

### Post by ocli5568 on 2013-05-23
Unfortunately this didn't work.

I have the linux headers and build essential packages (up to date) and reinstalling the graphics driver didn't help either.

---

### Post by HiImTye on 2013-05-23
check your logs to see if there are any graphics errors

```
less /var/log/syslog && less /var/log/kern.log
```

---


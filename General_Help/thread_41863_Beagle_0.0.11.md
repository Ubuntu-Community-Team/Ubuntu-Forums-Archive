---
title: "Beagle 0.0.11"
date: 2005-06-15
forum: General Help
---

### Post by manicka on 2005-06-15
Beagle 0.0.11 is out. Has anyone had any success compiling and installing it?

---

### Post by xvlun on 2005-06-15
yes, no problems

---

### Post by XDevHald on 2005-06-15
> Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.

I started the daemon with beagled as the user not as root just incase if anyone was wondering. But when I installed the packages they told me to install, they worked, but now I am not able to find the beagle log file on my system. Odd?

---

### Post by manicka on 2005-06-15
[QUOTE=xvlun]yes, no problems[/QUOTE]
could you briefly outline what you did to get it working

thanks

---

### Post by xvlun on 2005-06-15
i just downloaded the sources and did 
./configure
make
make install
that was it. btw. im using mono from sarge unstable mono repositories and some other deps from breezy.

---

### Post by willrea on 2005-06-15
when doing ./configure I get this:

./configure: line 645: syntax error near unexpected token `beagle,'
./configure: line 645: `AM_INIT_AUTOMAKE(beagle, 0.0.11)'

---


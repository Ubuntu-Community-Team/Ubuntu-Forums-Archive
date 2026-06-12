---
title: "remmina crashing after software update"
date: 2015-02-25
forum: General Help
---

### Post by ccurvey on 2015-02-25
I had the software update messages come up today, so I dutifully installed them.  They asked for me to restart my machine, and I complied.  Now remmina can establish a connection to my windows desktop, but as soon as I click "OK", remmina crashes.  /var/log/kern.log contains

Feb 25 14:11:05 mu kernel: [  799.720381] remmina[9607]: segfault at 7fd2502698b8 ip 00007fd26d984b7c sp 00007fd25bb50560 error 6 in libc-2.19.so[7fd26d903000+1ba000]

I've been able to duplicate the problem in Unity, Cinnamon and Cinnamon w/ Software Rendering.

---

### Post by ccurvey on 2015-02-25
weirdness...I tried rdesktop as well, and got a crash at the same point, with this kernel log:

Feb 25 14:24:30 mu kernel: [ 1604.774090] vinagre[10787]: segfault at 17794e0 ip 00007f3004b51891 sp 00007ffff03bea40 error 6 in libc-2.19.so[7f3004ad0000+1ba000]

But then I tried again, and things seem to be working in both remmina and rdesktop.

---

### Post by Yobibyte on 2015-03-04
I have been running into this same problem and it was severely interfering with my work. I haven't found a proper solution, but have switched to FreeRDP instead. 

[https://github.com/FreeRDP/FreeRDP/wiki/CommandLineInterface](https://github.com/FreeRDP/FreeRDP/wiki/CommandLineInterface)

[https://launchpad.net/ubuntu/+source/freerdp](https://launchpad.net/ubuntu/+source/freerdp)

---


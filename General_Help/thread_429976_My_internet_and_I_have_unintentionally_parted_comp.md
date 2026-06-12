---
title: "My internet and I have unintentionally parted company..."
date: 2007-05-01
forum: General Help
---

### Post by fourthdimension on 2007-05-01
Hey All

I installed ubuntu about two weeks ago, and up till now it's been working perfectly, but today I just lost all internet.  I looked into the problem for a while, and I found it's not a hardware problem (I have internet access with a live CD on the same machine) and it's not a browser problem (multiple browsers won't connect, as is with other applications).  Before I reinstall my OS, does anyone have any idea of what could have gone wrong, or if I could have removed an essential file/program when I uninstalled some other programs through synaptic?  (that could be more than possible because although I'm a bit of a geek, I'm still very new to linux and don't recognize many process/program names yet) :lolflag: 

Thanks for taking the time to read this.

4-D

---

### Post by dcstar on 2007-05-01
> **fourthdimension said:**
> Hey All

I installed ubuntu about two weeks ago, and up till now it's been working perfectly, but today I just lost all internet.  I looked into the problem for a while, and I found it's not a hardware problem (I have internet access with a live CD on the same machine) and it's not a browser problem (multiple browsers won't connect, as is with other applications).  Before I reinstall my OS, does anyone have any idea of what could have gone wrong, or if I could have removed an essential file/program when I uninstalled some other programs through synaptic?  (that could be more than possible because although I'm a bit of a geek, I'm still very new to linux and don't recognize many process/program names yet) :lolflag: 

Thanks for taking the time to read this.

4-D

Open a terminal and do the following commands (post the results):
```
[B]ifconfig
netstat -r[/B]
```

---

### Post by fourthdimension on 2007-05-01
Thanks.  Here's the results:

```
my username:~$ iconfig
bash: iconfig: command not found
my username:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
192.168.200.0   *               255.255.255.0   U         0 0          0 vmnet1
192.168.94.0    *               255.255.255.0   U         0 0          0 vmnet8
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

---


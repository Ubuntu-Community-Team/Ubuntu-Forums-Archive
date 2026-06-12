---
title: "udevd[355]: timeout: killing /sbin/modprobe -bc pci:XXXXXXXXXXXXXXXXXX"
date: 2013-05-02
forum: General Help
---

### Post by frohfroh on 2013-05-02
Hi,

I have a dual boot laptop with Windows 7 and Ubuntu 12.10 installed on  it. It´s been working fine for like 6 months. I don´t know what it its  that I have installed or updated that now I cant get to Ubuntu: It goes  goes ubuntu purple and then black and thats it.
When I try loading on safe mode, I reach a point where I get the message  above and it goes on and on.   Ive looked on the internet for the message above and tried tracking down  the problem on syslog or kern.log, but I cant find it.
It does have two graphic cards, but it was working fine till yesterday.
My problem is exactly the same as the one described at [http://ubuntuforums.org/showthread.php?t=2135990](http://ubuntuforums.org/showthread.php?t=2135990) , but as that thread is marked as solved, I created a new one. BTW, Boot Repair did not solve the problem.

---

### Post by zeimusu on 2013-05-11
Similar issues here. It made regular booting very slow (as it was waiting for the timeout) and I had hanging on shutdown and suspend, and it spews the above error message 
I worked around it by downgrading to an older kernel, 3.8 was causing the problem for me but 3.5 works ok. (I still had 3.5 around, so I only had to uninstall the linux-image 3.8..., I tested by choosing the older kernel with from grub before uninstalling anything)

lspci -s XX:XX.X may tell you what is causing the problem. (XX:XX.X as in the error message)

---


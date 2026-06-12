---
title: "Hrtimer Support for kernel-3.2.0.23"
date: 2013-03-25
forum: General Help
---

### Post by gauravks72 on 2013-03-25
Hello All,

I am newbie to linux. Currently i am developing kernel modules using ubuntu 12.04. I installed linux-image-3.2.0-37-lowlatency-pae and linux-image-3.2.0-23-realtime-pae using apt-get commands since I require an RT_PREEMPT enabled kernel for testing my module.

In these versions i was not able to find the [COLOR=#b22222]**sirq-hrtimer**[/COLOR] thread in the ps aux list which is present in ubuntu 10.04 version (2.6.31-11-rt). I need this thread to test my module.

Can anyone tell me whether i need to install some other packages with these versions to enable this thread or the sirq-hrtimer has been renamed in latest kernel?

Thanks in advance.

---


---
title: "&quot;The system is running in low-graphics mode&quot; after Ubuntu upgrade"
date: 2017-02-14
forum: General Help
---

### Post by rgriffin30185 on 2017-02-14
Hi,

My system was working fine until I upgraded from Ubuntu 12.04 to 14.04. It won't boot up and displays "The system is running in low-graphics mode".

I'm a newbie with Linux and need a few pointers on how to fix this issue.

Just so you know I am running the OS on a Desktop. I cannot access the internet on the PC because the network that I am connected to is the company network and we use a Cyberoam Device Proxy which I need to login using the client to access the internet. One way which I can be able to access the internet is via the Cyberoam client URL using a web browser however since I am stuck using terminal I am not familiar on how to use terminal to run the URL and put in my username and password to connect to the internet.

Any ideas????

---

### Post by wildmanne39 on 2017-02-14
*Thread moved to **General Help**.*

---

### Post by wildmanne39 on 2017-02-14
Please post the output of:
```
lspci | grep VGA
```
Thanks

---

### Post by rgriffin30185 on 2017-02-15
As requested here is the output below:

*VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev09)*

---

### Post by rgriffin30185 on 2017-02-17
Well after trying various ideas to resolve the issue all was in vain.

I've created a bootable USB of Ubuntu 16.04 and installed on the PC and works fine now. Closing this thread for now.

---


---
title: "really low resolution on the ps3"
date: 2008-04-07
forum: General Help
---

### Post by devin0 on 2008-04-07
Hi, i just installed  ubuntu on my ps3. Everything is working fine, except 
the resolution is low. How do I make the resolution higher?

---

### Post by articpenguin on 2008-04-07
do you have a High Defination TV or standard definiation? If you have a SD (standard TV) the i you cant go above 800x640.

IF its HD tv then i dont know how to make it bigger.

---

### Post by shadyedsan on 2008-04-07
try the following in terminal:

sudo dpkg-reconfigure xserver-xorg

follow the steps and select which refresh rate you want and what resolution. i think high resolution is only available with hdtv's but i'm not sure.

---

### Post by shadyedsan on 2008-04-07
> **shadyedsan said:**
> try the following in terminal:

sudo dpkg-reconfigure xserver-xorg

follow the steps and select which refresh rate you want and what resolution. i think high resolution is only available with hdtv's but i'm not sure.

you might want to look at [www.psubuntu.com](www.psubuntu.com) for help over on their forums

---

### Post by ikonia on 2008-04-07
ubuntu on the PS3 will be very limited due to lack of native hardware access as ubuntu will be run through almost a "Vm" controlled by the PS3 hypervisor.

---

### Post by devin0 on 2008-04-09
Ok, i checked what resolution i am using. i go to screen resolution and the only option is 576x384 at 30 hz as the refresh rate. is there any way to set a higher resolution?

---


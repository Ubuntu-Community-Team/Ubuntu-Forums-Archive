---
title: "network problem after chmod"
date: 2008-05-06
forum: General Help
---

### Post by cibi81 on 2008-05-06
Hi guys,
I had the insane idea to perform a "sudo chmod --recursive 775 /usr" , (that i thought to be safer than the "sudo chmod --recursive 775 / " i tried to do previously), and suddenly network does not work anymore. I have a LAN enterprise network with a proxy and I run ubuntu 7.10 inside virtualbox.   
The network icon is a round spinning arrow and the tooltip says: "requesting a network address from wired network".
If I perform ifconfig eth0, there is a sospiciuos:
 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

please help!
Don't tell me I have to reinstall ubuntu!

Thanks
Angelo

---

### Post by fahadsadah on 2008-05-06
> **cibi81 said:**
> Hi guys,
I had the insane idea to perform a "sudo chmod --recursive 775 /usr" , (that i thought to be safer than the "sudo chmod --recursive 775 / " i tried to do previously), and suddenly network does not work anymore. I have a LAN enterprise network with a proxy and I run ubuntu 7.10 inside virtualbox.   
The network icon is a round spinning arrow and the tooltip says: "requesting a network address from wired network".
If I perform ifconfig eth0, there is a sospiciuos:
 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

please help!
Don't tell me I have to reinstall ubuntu!

Thanks
Angelo
Try chmoding it back to 755. That should fix it, but if not, then I'm sorry, but you need to reinstall.
Why on earth did you do it?

---

### Post by cibi81 on 2008-05-06
I'm going to try. Thank you!

Why did I do it? It' a long story. I installed ubuntu 8.04 but I had some problem to configure monitor and play videos and i saw no improve respect to 7.10 except for firefox 3.
So I decided to install back ubuntu 7.10, installing firefox 3 with a "work around", but in order to install flash player plugin I need /usr and /usr/lib and /usr/lib/mozilla writable, and they were not. I thought to have /usr writable by the user were not a problem, in fact to be "able to write" does not mean that "I will write". I know i have been an idiot !!!

Thank you for your help!

---

### Post by cibi81 on 2008-05-07
It didn't help! I am going to re-install
Thank you anyway.

---


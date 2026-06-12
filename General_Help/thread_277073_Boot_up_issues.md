---
title: "Boot up issues"
date: 2006-10-13
forum: General Help
---

### Post by bensr20det on 2006-10-13
Alright I just installed ubuntu 6.06 and did all my updates. I have a wireless card in my box but I am hardwired to my router. After that I reboot the box and everything went fine. I then setup the wireless just to make sure that it worked I then reboot the system again. Now it locks up when it gets to "configuring network interfaces..." on the boot up screen. If I open the box and remove the wireless card it boots right up. And if I put the card back in it locks up on the same part of the boot up.

Is there a way that I can reset the network interfaces?

---

### Post by K.Mandla on 2006-10-14
It's possible Ubuntu is trying to find a network, and sits there waiting while nothing responds. I can recall seeing it do that with a wireless card I had misconfigured. It's possible (but never certain) that waiting a while might convince it there's nothing there, and it will continue the startup procedure.

In general I think you can restart your network with 

```
sudo /etc/init.d/networking restart
```
If you want to get into the real dirt, try editing the /etc/network/interfaces file. You'll be able to modify which network interface is enabled, and which is ignored.

Hope that helps.

---

### Post by jalm111 on 2006-10-14
If you take it out of interfaces (comment out with #) it won't look for it. 

Are you trying to use the wireless card?

What model is it, are you using native drivers or ndiswrapper?

---

### Post by bensr20det on 2006-10-14
No i don't really care to use the wireless. I wil try to reset it and let you know.

---


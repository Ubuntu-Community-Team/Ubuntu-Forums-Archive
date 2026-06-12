---
title: "Have two Ethernet connections (both Eth0) in &quot;Network Connections&quot; Make one default?"
date: 2015-08-19
forum: General Help
---

### Post by 777funk on 2015-08-19
I have two different connections in "Network Connections". Is there a way to make one default upon startup? See the screen shot for clarity.

 [ATTACH=CONFIG]263944[/ATTACH]

---

### Post by TheFu on 2015-08-19
Disable the one you don't want.  Perhaps there is a better way to achieve what you need with a single connection?

For example, it is common to want a static IP at home, but still be able to use DHCP when outside the home.  Most home routers support DHCP reservations. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains a little more.

Of course, there are hundreds of other needs that cannot be met easily, but there are many ways to script and hence, automate different connection requiremtns.

---

### Post by 777funk on 2015-08-19
That's exactly what I'm using it for (static IP at home and I need another IP for testing of a piece of gear). I'd like it to default to my home's static IP.

---

### Post by TheFu on 2015-08-19
> **777funk said:**
> That's exactly what I'm using it for (static IP at home and I need another IP for testing of a piece of gear). I'd like it to default to my home's static IP.

So - setup the home router with a DHCP reservation for this device to a specific, static, IP. Then you only need 1 config and can delete the other. That will solve the root cause.

---

### Post by 777funk on 2015-08-19
That's been done and is one of the two settings I have there. But I frequently have a need to change my computer's Eth0 connection to the other saved setting. The other is the setting I use for testing some wireless gear (requires it's own parameters which is what is in the other saved setting). 

So, I need both settings. I just don't want the testing setting to be my default since it doesn't work for my day to day.

---


---
title: "Eth0 connection requires reenabling after each restart - for the love of god, why?"
date: 2005-11-02
forum: General Help
---

### Post by monomaniacpat on 2005-11-02
For some reason my ethernet connection will only work if I disable and then reenable my connection under networking - is there some way to make Ubuntu do it automatically, or other such solution?

Yours,


Mono.

---

### Post by ecobuntu on 2005-11-02
yup

sudo gedit /etc/network/interfaces

Add these lines

auto eth0
iface eth0 inet dhcp

---

### Post by monomaniacpat on 2005-11-02
Thanks for that. Unfortunately I seem to already have those lines inserted. I'll see how it works after a restart...

---

### Post by ecobuntu on 2005-11-02
I don't know what it would be other then that.  If you are running a laptop you could try to install laptop-net.  That will automatically run dhcp

sudo apt-get install laptop-net

---

### Post by jvictor on 2005-11-03
During boot up does the step

Bringing up network interfaces fail ?

Do u use DHCP ? 

If u r using a DSL Router and just one comp try static ip config

Is ur machine a laptop ?

---

### Post by crowndip on 2005-11-03
Hi,

try to put it there the other way round


iface eth0 inet dhcp
auto eth0

By the way, if you make changes using the grafical network manager, it should reflect the changes in this file.

---

### Post by monomaniacpat on 2005-11-05
thanks for the help! Unfortunately I've tried it both way round, but I still have to enable/ reenable each time. Is there anything else I can try?

---

### Post by nightfly on 2005-11-05
Ubuntu system activates your ethernet connection during boot time by default. And it should be fine if you have the network cable plugged in.

Exactly what is the procedure you follow to reenable the connection after restart ?

---

### Post by monomaniacpat on 2005-11-06
I go to System-> Administration -> Networking and click deactivate, activate.

I'm going to try restarting with the cable plugged in from the beginning - it's possible I've put it in too late previously!

---


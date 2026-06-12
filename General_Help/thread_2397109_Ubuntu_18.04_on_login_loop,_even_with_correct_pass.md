---
title: "Ubuntu 18.04 on login loop, even with correct password"
date: 2018-07-25
forum: General Help
---

### Post by wowbaggerbr on 2018-07-25
Guys, I installed Ubuntu 18.04 yesterday, done some app installation and configurations and went to sleep. This morning, the login simply didn't work: the system is unable to log into my session, even with the correct password. Every time I try it, it flashes the screen into black and purple, the mouse pointer is available, but it flashes back to the login screen again: no error message prompts and I spent quite some time amusing myself trying to win it by attrition =). I also tried switch over to Wayland, and the same result: screen flashes to black, couple of seconds later, I'm back at the login stage.

There is nothing wrong with my password, since I can log into my user account on the Terminal (CTRL+ALT+F1). Once there, I did a sudo apt update/upgrade in the hopes it'd fix something, but my system was up to date and it didn't solve anything after I rebooted.

I've seen a lot of similar reports on the internet and the only solution that it seemed worthwhile to my noobish eyes was removing/deleting the .Xauthority file. But when I tried it, the return I got was that there was no such file on my Home directory. The other solutions applied to people upgrading their systems - mine was a fresh install - or with pretty specific hardware and conditions that don't apply to me.

So, what should I do to fix this?

---

### Post by Frogs Hair on 2018-07-25
Hello and Welcome:

Automatic log-outs are often graphics card or hardware related it may help to provide some information about your system.

---

### Post by wowbaggerbr on 2018-07-26
It's a Dell Inspiron 7560 (since Dell sells this with Ubuntu installed, should be well supported, doesn't it?). The specs are:

Core i7 7500U
Nvidia Geforce 940MX

I got the Nvidia driver through the Software and Updates app. Since I rarely use the discrete GPU in order to prevent overheating and battery drainage, I did the "prime select intel" thing to switch over to the iGPU. It booted fine under the Intel GPU during my updates and reboots after some apps installations.

---


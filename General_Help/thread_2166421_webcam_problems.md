---
title: "webcam problems"
date: 2013-08-09
forum: General Help
---

### Post by aiden707 on 2013-08-09
Hi 
i have got a logitech c910 webcam, it works with guvcam . But skype and cheese dont work both have black screens, please can someone help. 
In a terminal i typed - sudo lsusb
and this was the output

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 15d9:0a4d Trust International B.V. 
Bus 001 Device 014: ID 046d:0821 Logitech, Inc. HD Webcam C910
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver


If anyone could help it would be great as i really want skpe to work
thanks

---

### Post by aiden707 on 2013-08-20
):p

---

### Post by papibe on 2013-08-20
Hi aiden707.

It may a problem with with the Logitech Unifying Receiver. There are several alternatives to add support for it. Take a look a this: [Is Logitech's Unifying receiver supported?]("http://askubuntu.com/questions/113984/is-logitechs-unifying-receiver-supported")

I'd recommend using **solaar** which is available using a ppa.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by aiden707 on 2013-08-20
thanks, i will read link

---

### Post by aiden707 on 2013-08-20
i installed solaar, i have a logitech wireless keybord which i disabled to see if it make a difference. Now i cant get that to work or show in solaar ( and webcam still not working)
help

---

### Post by papibe on 2013-08-20
Did you try the old preload trick?

First you need to know the path of v4l1compat.so in your system:
```
dpkg -S v4l1compat.so
```
I'm running Ubuntu 64bits so it returns:
```
libv4l-0:i386: /usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
libv4l-0: /usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
```
Then you need to know if Skype is 32b or 64b:
```
file $(which skype)
```
If it is 32bits, it will return something like:
```
/usr/bin/skype: ELF **[COLOR="#FF0000"]32-bit[/COLOR]**...
```
Then, you preload the 32bit video library while calling Sype from the terminal:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so  skype
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by aiden707 on 2013-08-21
thanks, but i need to get the keybord working again first (using old keybord at mo). When i disabled the keybord in solaar, i cant get it back working.I have reinstalled ubuntu so is a clean system but the wireless keybord is still not working. ( when i first got the keybord it worked as soon as i plugged it in) any idea?

---

### Post by aiden707 on 2013-08-25
thanks 

papibe for trying to help. i have formated system and done clean install ( took me a few days to work out how to do that), and now c910 webcam works perfect as does k400 keybord. I still dont understand ternimal commands, any ideas on good site to learn from so i dont just copy and paste i understand what i am typing.

---

### Post by papibe on 2013-08-25
Here's a good selection of links: [Command Line Resources]("https://help.ubuntu.com/community/CommandLineResources").

Regards.

---


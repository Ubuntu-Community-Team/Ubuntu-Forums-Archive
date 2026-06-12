---
title: "can anyone help me install etherape?"
date: 2017-10-23
forum: General Help
---

### Post by ortermagic on 2017-10-23
when I try to open etherape I get this, ever since I upgraded to artful.

```
ortermagic@ortermagic:~$ sudo etherape
[sudo] password for ortermagic: 
Invalid MIT-MAGIC-COOKIE-1 key
(etherape:11605): Gtk-WARNING **: cannot open display: :0
unexpected EOF in read_all()
critical: read_all() failed on control socket
ortermagic@ortermagic:~$ 


```

what is this magic cookie?

---

### Post by #&amp;thj^% on 2017-10-23
> =ortermagic;13702085

what is this magic cookie?


A magic cookie, or just cookie for short, is a token or short packet of data passed between communicating programs, where the data is typically not meaningful to the recipient program. ... The cookie is often used like a ticket &#8211; to identify a particular event or transaction.
See this for more info: [https://en.wikipedia.org/wiki/Magic_cookie](https://en.wikipedia.org/wiki/Magic_cookie)

I suspect this happening on a Wayland Login correct?
Bugs have been filed: [https://bugs.launchpad.net/ubuntu/+source/etherape/+bug/1650801](https://bugs.launchpad.net/ubuntu/+source/etherape/+bug/1650801)

---

### Post by ortermagic on 2017-10-23
That's not really very helpful, I have no knowledge of "wayland" aside from what I learned from your links.
Before the 17.10 upgrade I was able to run etherape from the terminal. I haven't consciously installed anything wayland
```
ortermagic@ortermagic:~$ sudo etherape
[sudo] password for ortermagic: 
Invalid MIT-MAGIC-COOKIE-1 key
(etherape:12648): Gtk-WARNING **: cannot open display: :0
unexpected EOF in read_all()
critical: read_all() failed on control socket
ortermagic@ortermagic:~$ 


```
What does MIT-MAGIC-COOKIE-1 key imply?

---

### Post by #&amp;thj^% on 2017-10-23
Guess you would have to know what Wayland is first.
```
echo $DESKTOP_SESSION

```
Return the output from above code PLEASE

Wayland and Ubuntu: [https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

Before running GUI application enable root access to display server:
```
xhost +SI:localuser:root

```
**I hesitate to give this work around for safety concerns.** [COLOR="#FF0000"](You have been warned use at your own risk)[/COLOR]
But it will only last for the running session.
I made an alias to my .bashrc for these  occasions.
Good Luck

---

### Post by ortermagic on 2017-10-24
Desktop session returns

```
ortermagic@ortermagic:~$ echo $DESKTOP_SESSION
ubuntu
ortermagic@ortermagic:~$ 




``` 
```
xhost +SI:localuser:rootxhost +SI:localuser:root
```

I think it worked, thank you! I am having a problem attaching a screenshot tho. Hang on I've got it

[ATTACH=CONFIG]277246[/ATTACH]

---

### Post by ortermagic on 2017-10-24
It worked once but has since reverted back I got the following before a restart...

```
ortermagic@ortermagic:~$ sudo etherape
[sudo] password for ortermagic: 
/usr/share/themes/Ambiance/gtk-2.0/apps/mate-panel.rc:30: error: invalid string constant "murrine-scrollbar", expected valid string constant
EtherApe-INFO: sctp protocol not supported
EtherApe-INFO: ddp protocol not supported
EtherApe-INFO: ddp protocol not supported
EtherApe-INFO: ddp protocol not supported
EtherApe-INFO: ddp protocol not supported
EtherApe-INFO: get_interface result: ''
EtherApe-INFO: Available interfaces for capture: usbmon9 usbmon8 usbmon7 usbmon6 usbmon5 usbmon4 usbmon3 usbmon2 usbmon1 nfqueue nflog lo any enp2s0
EtherApe-INFO: Link type is Ethernet
EtherApe-INFO: Diagram started

(etherape:4508): IBUS-WARNING **: The owner of /home/ortermagic/.config/ibus/bus is not root!
ortermagic@ortermagic:~$ 
```

and after the restart I was back to this ...

```
ortermagic@ortermagic:~$ sudo etherape
[sudo] password for ortermagic: 
Invalid MIT-MAGIC-COOKIE-1 key
(etherape:1820): Gtk-WARNING **: cannot open display: :0
unexpected EOF in read_all()
critical: read_all() failed on control socket
ortermagic@ortermagic:~$ 
```

could you analyse this please.

---

### Post by ortermagic on 2017-10-25
Thanks to ncweber, [https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077), your tip has solved my problem.
someone help me find the "solved" tag please. 
Oh okay! I found the thread tools.

---


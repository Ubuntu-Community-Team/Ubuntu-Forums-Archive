---
title: "Boot is too slow"
date: 2007-05-02
forum: General Help
---

### Post by Boobek on 2007-05-02
Hello!
This is not a big problem, but problem...
So! I have an Amilo Pi 1505 laptop ( core duo, intel grapich, fujitsu siemens motherboard ) and when I boot the system, The machine is wait more secounds with no activity:( 
(example : first 20 sec here is apci: interrupt link IRQs ... *5)
I post my bootchart 'log':p
pls add tipps me!

(Sorry for my english)

---

### Post by m.musashi on 2007-05-02
Nice chart but I'm not sure what it means. I did notice that on my laptop with Feisty it stalls during the boot. I turned off the graphical boot and saw it was related to network interfaces. Basically, it tries to connect but with wireless it can't so it waits until it times out. You might see if that seems to be your problem. If so, edit the /etc/network/interfaces file
```
sudo gedit /etc/network/interfaces
```
and comment out all items except
```
auto lo
iface lo inet loopback
```
That worked for me. That way it waits until log in to connect to wireless.

---

### Post by Boobek on 2007-05-03
Hello!
Thank you, for the answer, but my problem is another.... the boot up process time do not shorter!
(and the gnome doesn't started I think the bug is in the nm-applet)
Another way?

---


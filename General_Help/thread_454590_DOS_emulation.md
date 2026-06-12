---
title: "DOS emulation"
date: 2007-05-25
forum: General Help
---

### Post by sas13 on 2007-05-25
I have an old DOS program that I need to get running under ubuntu. The program communicates with a remote piece of electronics via a modem connected to a serial port.

It's nothing too fancy, but it seems that most DOS emulation programs such as DOSbox are geared towards gaming and don't have much networking support, so I was hoping someone here might have some experience and be able to help me out.

Thanks!

---

### Post by akudewan on 2007-05-26
You could try out dosemu, or maybe Qemu.

Edit: have a look at this: [http://dosemu.sourceforge.net/docs/README/0.98/README-16.html](http://dosemu.sourceforge.net/docs/README/0.98/README-16.html)

---

### Post by sas13 on 2007-05-27
Interesting, thanks.

That link might have the solution. But it makes me realize that I don't really know how to access the modem on the serial port via ubuntu (without the DOS emulation), which I will need to do to test my setup.

So to hijack my own thread - any tips on how I would use ubuntu to access an etherpath  modem connected to a serial port? This needs to be done on a machine simultaneously connected to a LAN via its ehternet port.

---

### Post by akudewan on 2007-05-28
I can't help you much there. Maybe the usual method of gnome-ppp may help ?

---

### Post by sas13 on 2007-05-28
OK, after doing a little more searching, reading and playing around I think I can describe my problem a little better -

I need to allow a DOS program to access a serial port. Connected to this serial port is an etherpath server/client pair in "nailed up" mode, connecting it to a remote piece of electronics. (This is a way of tricking the computer into thinking its serial port is connected directly to the remote electronics, when in fact the etherpaths allow the communications to travel via the net.)

I'm describing the whole setup as background, but all I really need to do is allow acces to the serial port, it really has nothing to do with what that port is connected to.

So I'm afraid standard ppp tools or the link regarding networking and dosemu aren't the way to go - my program needs to access a serial port, not a network.

---

### Post by sas13 on 2007-05-28
I've been trying to solve this using dosemu, but I can't really get it to work.

My DOS program reports it is unable to access COM1. When I run dosemu using the -s switch (running it as root) it gives the following message:
> Running privileged (sudo/suid) in full feature mode
Dropping root privileges: guest or a restricted user not on console.

I tried to edit /etc/dosemu/dosemu.conf to add the serial port settings - > $_com1 = "/dev/ttyS0 irq 4"
or to add the port number - >  $_ports = "0x03f8"
 $_irqpassing = "4"

but all that does is give me a dosemu error:> ERROR: SERIAL: Unable to open device /dev/ttyS0: Permission denied

I have also edited the dosemu.users file to allow all class permissions, but with no change in the results.

Any ideas?

---


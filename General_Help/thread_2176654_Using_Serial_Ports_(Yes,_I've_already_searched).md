---
title: "Using Serial Ports (Yes, I've already searched)"
date: 2013-09-25
forum: General Help
---

### Post by toby-richards-w on 2013-09-25
I have searched for this off and on for a few years. Every time I try to look up how to use serial ports in Linux, the results are all about how to serve up a console over a serial port. That is not what I want to do.

Can anybody tell me how to connect to another device--such as a Cisco switch--with my serial port? I'm sure there are GUI apps for this, but I want to do it with the command line (to include specifying bps, stop bits, parity, flow control, etc.).

Thanks!

---

### Post by Kirboosy on 2013-09-25
Welcome to the Ubuntu Forums!

I found a program called Minicom that should do what you want.

[Minicom -- Community Ubuntu Documentation]("https://help.ubuntu.com/community/Minicom")

Hope that helps!
~Caboose

---

### Post by Lars Noodén on 2013-09-26
Another one, is [cu](http://manpages.ubuntu.com/manpages/raring/en/man1/cu.1.html).  Either way, you have to know the speed (and other connection options) and TTY device.  For me to connect at 19200,8,N,1 (that is 19200 bits per second, 8-bit word length, no parity, 1 stop bit) using a USB-to-serial adapter on ttyUSB0, I would run the following:

```

cu -s 19200 -l /dev/ttyUSB0

``` 

Your actual speed may be different for your device.  Your serial device will be different, but it will probably be somewhere in /dev/tty* if it is a built-in serial port.

You may also have to add your account to the group *dialout*.  If you do, you have to log out and log in again for the changes to take effect.

---


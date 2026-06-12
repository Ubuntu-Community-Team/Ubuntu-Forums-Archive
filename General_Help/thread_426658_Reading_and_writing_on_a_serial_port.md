---
title: "Reading and writing on a serial port"
date: 2007-04-28
forum: General Help
---

### Post by orlox on 2007-04-28
Hi.

I'm looking for an app that lets me read incoming data in a certain serial port, and send data through that same port.

Does anyone know of a good one??

---

### Post by acormack on 2007-04-28
I use php for serial comms that works vey well as a general purpose scripting language from the command line.

It really depends which programming languages you like.

[http://uk.php.net/manual/en/function.fopen.php](http://uk.php.net/manual/en/function.fopen.php)

---

### Post by orlox on 2007-04-28
Actually, I'm not looking for a way to program the serial communication. I'm just looking for an application that allows me to see what is being read from a certain serial port, and that allows me to write data to that port.

I've seen applications like these for windows, but don't know of a similar app for linux.

---

### Post by acormack on 2007-04-29
How about:

apt-get install ttylog

---

### Post by orlox on 2007-04-29
Thanx, but I just found this:

[http://cutecom.sourceforge.net/](http://cutecom.sourceforge.net/)

It's a simple qt based program that works exactly as I want....

---

### Post by dcstar on 2007-04-30
> **orlox said:**
> Thanx, but I just found this:

[http://cutecom.sourceforge.net/](http://cutecom.sourceforge.net/)

It's a simple qt based program that works exactly as I want....

Is it anything like **gtkterm** which is available in the Ubuntu repositories?

---


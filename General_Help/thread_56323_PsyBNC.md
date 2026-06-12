---
title: "PsyBNC"
date: 2005-08-12
forum: General Help
---

### Post by [_Silence_] on 2005-08-12
Hey,
 I'm trying to setup a PsyBNC on my Ubuntu instalation, but since Ubuntu has all ports closed by default there aren't any ports listening to run my PsyBNC. Anyone knows how I can make a listening port?

---

### Post by pmj on 2005-08-12
All I had to do to connect to psyBNC was having my router forward a port for it, Ubuntu itself wasn't blocking anything. Are you using a firewall?

I apologize if this wasn't particularly helpful. psyBNC isn't a very commonly used piece of software so I was afraid you wouldn't get any other answers.

I hope you have better luck setting it up than I did. I'm stuck where it asks for a password. :)

---

### Post by [_Silence_] on 2005-08-12
[QUOTE=pmj]All I had to do to connect to psyBNC was having my router forward a port for it, Ubuntu itself wasn't blocking anything. Are you using a firewall?

I apologize if this wasn't particularly helpful. psyBNC isn't a very commonly used piece of software so I was afraid you wouldn't get any other answers.

I hope you have better luck setting it up than I did. I'm stuck where it asks for a password. :)[/QUOTE]

 Not using firewall, but using a router. The port is open in the router but Ubuntu seems to be blocking it. =( Tried many ports already, all closed.

---

### Post by pmj on 2005-08-12
I hope you know that the psyBNC process has to be killed and restarted every time you change any settings. Also, if you had the same problem that I did with the GUI configuration crashing you might have to manually edit the config file to make sure psyBNC is using the right port.

I really don't know what else to say. I hope it's just an issue with Ubuntu and that someone else here knows how to fix it.

---

### Post by madmonk3y on 2007-06-12
You set the listening port in make menuconfig, or in psybnc.conf

I also posted what packages are needed to compile psybnc here:

[http://ubuntuforums.org/showpost.php...16&postcount=5](http://ubuntuforums.org/showpost.php...16&postcount=5)

But you will also want to have a look at this:

[http://ubuntuforums.org/showpost.php...53&postcount=1](http://ubuntuforums.org/showpost.php...53&postcount=1)

... because even if you get psybnc compiled, it probably won't run as expected.

---

### Post by dinasty on 2007-06-16
> **madmonk3y said:**
> You set the listening port in make menuconfig, or in psybnc.conf

I also posted what packages are needed to compile psybnc here:

[http://ubuntuforums.org/showpost.php...16&postcount=5](http://ubuntuforums.org/showpost.php...16&postcount=5)

But you will also want to have a look at this:

[http://ubuntuforums.org/showpost.php...53&postcount=1](http://ubuntuforums.org/showpost.php...53&postcount=1)

... because even if you get psybnc compiled, it probably won't run as expected.


You links dosen't work, pls fix that, i need the help aswell

---

### Post by madmonk3y on 2007-06-20
[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---


---
title: "How do I make a live cd from my current ubuntu install? [Resolved]"
date: 2007-02-24
forum: General Help
---

### Post by Lanrat on 2007-02-24
Hi, I have been looking into making my own customized Ubuntu Linux live cd (or dvd).

I have Googled around and i found this

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06)

But I would like to install Ubuntu and then customize it, (settings, add/remove programs, etc...) and then make a live cd (or dvd) of that install.


Anyone know how to do this or have any ideas?
Is this even possible? (i am really certain it is)

---

### Post by Lanrat on 2007-02-24
Anyone?

---

### Post by disturbedite on 2007-02-24
bump

i'd like to know if this is possible too.

---

### Post by dcstar on 2007-02-24
> **disturbedite said:**
> bump

i'd like to know if this is possible too.

I have made a "Live" USB Pendrive persistent install using the instructions at:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I guess you could do something similar with a CD instead of the USB drive?

---

### Post by aysiu on 2007-02-24
I don't know how you can do it for an *existing* install, but you can customize a live CD with Reconstructor:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by Lanrat on 2007-02-24
it doesn't need to be an existing install, it could be a fresh 1. i just want to do this so that i can have full control over how the cd will work.

(it is is off topic, but i also need to know this. how do i install a .deb package just in the terminal?)

Thanks!

---

### Post by aysiu on 2007-02-25
> **Lanrat said:**
> it doesn't need to be an existing install, it could be a fresh 1. i just want to do this so that i can have full control over how the cd will work. Reconstructor is the program for you, then.

> (it is is off topic, but i also need to know this. how do i install a .deb package just in the terminal?) ```
sudo dpkg -i *packagename*.deb
``` You can also double-click the .deb file to install it.

---

### Post by disturbedite on 2007-02-25
thanks for that reply aysiu.

---

### Post by Lanrat on 2007-02-26
Thanks, i haven't had time to try it out yet, but i will soon and let you know.

---


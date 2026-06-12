---
title: "Interacting with a serial port"
date: 2013-02-04
forum: General Help
---

### Post by hundred1906 on 2013-02-04
How can I arrange to display all traffic received on a serial port and allow the transfer of keyboard entry to the same port.

Basically, to allow diagnosis of an ASCII based exchange protocol.

Pretty sure it must be straightforward but searching for the word "terminal" mainly provides topics relating to terminal commands.

---

### Post by efflandt on 2013-02-04
The usual method is minicom, but apparently there is an alternative:
```
efflandt@XPS8100-1204:~$ apt-cache search minicom
cutecom - Graphical serial terminal, like minicom
minicom - friendly menu driven serial communication program
```
However, that is if you are trying to manually interact with something on a serial port from a terminal. Not sure how you would listen in on serial traffic between the port and a local process unless the local process had some way to do that.

---

### Post by hundred1906 on 2013-02-05
Thanks for that and yes I am trying to manually interact with an external device on a serial port - a KNX interface. I will give minicom a try.

---

### Post by dcstar on 2013-02-07
> **hundred1906 said:**
> How can I arrange to display all traffic received on a serial port ......


```
sudo cat /dev/ttyX
sudo tee /dev/ttyX
sudo tail -n /dev/ttyX
```

---

### Post by hundred1906 on 2013-03-04
I ended up using Cutecom - for it's graphical interface.

First though it is necessary to ensure that your user is a member of dialout group. The relevant instructions are here 

[http://askubuntu.com/questions/217871/cannot-open-dev-ttys0-permission-denied-but-in-dialout-group](http://askubuntu.com/questions/217871/cannot-open-dev-ttys0-permission-denied-but-in-dialout-group)

Thanks to everyone that helped.

---


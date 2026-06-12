---
title: "how to find serial port"
date: 2007-01-05
forum: General Help
---

### Post by t_ras on 2007-01-05
I have a Gamatronic UPS.
I installed NUT and configured it.
It seemed to work but it was getting wrong status.
I tried to reconnect it after disconnecting the cable and it started (!?!?)
which probably means the driver or tty was wrong.
How can I know which device (tty I guess) is my serial port connected to?

thanks!

---

### Post by koenn on 2007-01-05
try
```
[root@oscar root]# dmesg | grep tty
```

and/or

```
[root@oscar root]# setserial -g /dev/ttyS[01]
```

you should see your serial ports (/dev/ttyS0 /dev/ttyS1 ...) + some info such as IRQ and I/O address

I don't know how you'd tell which ttyS is wich connector on your computer, nor how you configure the applications you mention.

---

### Post by t_ras on 2007-01-06
10x

---


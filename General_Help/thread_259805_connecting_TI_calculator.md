---
title: "connecting TI calculator"
date: 2006-09-17
forum: General Help
---

### Post by wr0x2 on 2006-09-17
I have a ti-83+, and I want to connect it to my computer so that I can pursue learning z80 assembly. Graphlink under wine and tilp do not work. Graphlink will not detect the calculator period, and tilp will see that it is on com2, however it always has an error in transmission when trying to connect. Anyone here have experience with this?

---

### Post by jonzep on 2006-09-18
Have you tried tilp?

```
apt-get install tilp
```

> TI calculator <-> PC communication program for X
TiLP is a Texas Instruments calculator <-> PC communication program for
Linux. It is able to use any type of link, like the original TI GRAPH-LINK
(both black and grey cables), the homemade "$4 serial link", or the
"$5 parallel link". It even supports the new TI GraphLink USB, using the
tiglusb kernel module. See [http://lpg.ticalc.org/](http://lpg.ticalc.org/).

With TiLP, you can transfer files from your PC to your Texas Instruments
calculator, and vice-versa. You can also make a screen dump, a backup, transfer
a backup to the calculator, or take control of your TI from your PC, or even
install a new version of AMS on your calc !

You might be interested in the tidev-modules-source package which allows you
to build a set of three kernel modules. These modules are three drivers for
different link cables (serial, parallel, USB) which require running TiLP with
root privileges. With these modules loaded and the appropriate rights on the
device nodes, this won't be necessary.

---


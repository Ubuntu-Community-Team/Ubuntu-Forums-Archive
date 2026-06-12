---
title: "Network bandwidth monitor tool needed"
date: 2018-01-05
forum: General Help
---

### Post by filister on 2018-01-05
I am looking for a tool, which could give me details about the network usage for a certain pre-defined interval, let's say 10 minutes. I want to know my Tx and RX consumption in this interval. Perfect will be if it could also report the min/max and avg network speed in this interval and export it to a text/csv file.

---

### Post by dragonfly41 on 2018-01-05
Looking at my installed GKrellM System Monitor 
Configuration (F1) > Builtins > Internet & Net
might possibly meet your requirements.

The server version gkrellmd returns data.

There are other monitoring tools if you search in Synaptic.

---

### Post by filister on 2018-01-05
I just need some simple tool, command line preferably, nothing fancy.

---

### Post by dragonfly41 on 2018-01-05
Perhaps this discussion will point you to a tool ..

[https://stackoverflow.com/questions/368002/network-usage-top-htop-on-linux](https://stackoverflow.com/questions/368002/network-usage-top-htop-on-linux)

---

### Post by ajgreeny on 2018-01-05
Vnstat might help though you may need to create a script to get information for such short time intervals as 10 - 15 minutes.

---

### Post by untrustytahr on 2018-01-05
Perhaps** *iftop***

---

### Post by Habitual on 2018-01-05
any of the sysstat package utilities?
sar....is one of those utilities.


also [Collectl]("http://collectl.sourceforge.net/Tutorial.html")

vnstat is by far the easiest and is not part of eitherpackag mentioned already.

```
sudo apt-get install vnstat
```

---


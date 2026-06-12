---
title: "IPs"
date: 2008-03-15
forum: General Help
---

### Post by MattyG on 2008-03-15
I need help! I need to be able to see the ip addres that are in contact with my network. Is there any program for linux that will do this? If not is there any for windows.

---

### Post by unutbu on 2008-03-16
If you want to find your own IP address, you can type
```
ifconfig
```
at a terminal command line. Look for the relevant network interface, and "inet addr".

If you want to know your IP as the outside world sees you, point your browser at
[http://www.whatismyip.com/](http://www.whatismyip.com/)

If you want to see what computers currently have connections with your computer, type
```
netstat
```

---

### Post by amingv on 2008-03-16
Just as a note to what unutbu said, netstat (which I think is what you want) works both in Linux and Windows (with some modification, of course).

You can use it like this:
```
netstat -n --ip | grep ESTABLISHED
```
also
```
man netstat
```

---


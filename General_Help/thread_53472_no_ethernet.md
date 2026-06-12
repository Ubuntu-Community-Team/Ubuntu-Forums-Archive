---
title: "no ethernet"
date: 2005-08-01
forum: General Help
---

### Post by sazplayer on 2005-08-01
when i ifconfig all it shows is my local network, no ethernet. so i pppoeconf which showed no ethernet card and recommended that i run modconfig which didn't work.
how do i get my machine to recognize the eth card? (i asked my local linux expert and he says he has solved this problem before but doesn't remember how).

---

### Post by Sam on 2005-08-01
Try
```
$ sudo ifup eth0
```

---

### Post by sazplayer on 2005-08-01
it gives

code:

sit0: unknown hardware address type 776
SIOCSIFADDR: no such device
eth0: ERROR while getting interface flags: no such device
eth0: ERROR while getting interface flags: no such device
sit0: unknown hardware address type 776
bind socket to interface: no such device
failed to bring up eth0

---

### Post by kleeman on 2005-08-01
You need to first check that the driver for your card is loaded. Find out what nic you have then google for the driver (name of nic plus linux usually does the trick). Once you know what the driver is check whether it is loaded with
sudo lsmod | grep XXXX
where XXXX is the driver name (or part of it).
If it isn't loaded then issue
sudo modprobe XXXX
and then use 
sudo ifconfig eth0 up
to bring up the interface
then go to the ppoeconf program as you discussed first.....

---

### Post by sazplayer on 2005-08-01
this is probably a stupid question but... how do i find out what nic i have?

---

### Post by kleeman on 2005-08-01
try 

lspci 

and look for the Ethernet controller line

---


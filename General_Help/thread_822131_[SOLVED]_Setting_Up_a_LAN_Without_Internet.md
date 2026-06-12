---
title: "[SOLVED] Setting Up a LAN Without Internet"
date: 2008-06-07
forum: General Help
---

### Post by yman on 2008-06-07
I have a laptop and a desktop. Both can only connect to a network using an Ethernet cable, and both have only one Ethernet port. The result is that if I want to connect them to each other, they have to be disconnected from the Internet. The network icons in the System Trays shows they are connected, but they don't seem able to communicate. I already know the laptop is able to share files with Windows with Samba, so what do I need to do to make this LAN work? And how do I do it?

The Desktop is Hardy, the Laptop is Dapper.

---

### Post by Herman on 2008-06-07
[Quick Simple SSH LAN]("http://users.bigpond.net.au/hermanzone/p11.htm#Quick_Temporary_SSH_LAN_"). - Connect two or more computers without internet, LAN or file rescue.

Regards, Herman :)

---

### Post by Shazaam on 2008-06-07
This might help......
[http://www.practicallynetworked.com/](http://www.practicallynetworked.com/)

---

### Post by yman on 2008-06-08
> **Herman said:**
> [Quick Simple SSH LAN]("http://users.bigpond.net.au/hermanzone/p11.htm#Quick_Temporary_SSH_LAN_"). - Connect two or more computers without internet, LAN or file rescue.

Regards, Herman :)
For both:
Subnet mask: 255.255.255.0
Gateway address: 255.255.255.255

Desktop: 198.45.45.66
Laptop: 199.45.45.66

Both gave error messages when sudo ifup -a. On Desktop:
```
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
SIOCADDRT: No such process
Failed to bring up eth0.

```
Although I got that error message when doing it when the 2 computers weren't connected to each other, because I stupidly closed the Terminal window. I'll post the error message from the Laptop later.

EDIT: Is giving a gateway address my mistake?

I installed SSH. This is now what I get on Desktop:
```
yman@Desktop:~$ sudo ifup -a
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
yman@Desktop:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

```
When trying to connect via ssh 198.45.45.66 from Laptop:
```

ssh: connect to host 198.45.45.66 port 22: Network is unreachable

```

---

### Post by cariboo on 2008-06-08
You have to change the ip address of one of the computers. The way you have it set up you are in two different subnets try:

```
Desktop  192.168.0.66
laptop  192.168.0.67
```

You will also need a crossover cable to connect the two. If you are going to spend the money on a crossover cable, for a few dollars more you can by a 4 port network hub. I'll leave the rest to your imagination.

Jim

---

### Post by yman on 2008-06-08
Thanks. It works now, and thanks to your help I was able to transfer all my files from my Laptop to my Desktop.

---


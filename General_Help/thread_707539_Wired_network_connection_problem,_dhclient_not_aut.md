---
title: "Wired network connection problem, dhclient not automatically run on bootup"
date: 2008-02-25
forum: General Help
---

### Post by mandana on 2008-02-25
Hi  all,

I am using Ubuntu on my desktop computer. I use eth0 to connect to the Internet.
However,sometimes I have to run the command "sudo dhclient eth0" to be able to connect to the Internet. It does not happen all the time on the startup, only sometimes.

Here is my /etc/network/interfaces:

auto lo
iface lo inet loopback


iface ath0 inet static
address 172.29.1.66
netmask 255.255.0.0
wireless-key A......F
wireless-essid VOICE

auto ath0

I added these lines into the file:

auto eth0
iface eth0 inet dhcp

but I could not connect to the Internet after this was done. Using 'ifconfig eth0' shows no IP address after this. So I removed the above lines again, and used the sudo dhclient eth0 again.

I've seen other people have similar issue, but I could not find any solution yet.It is interesting for me to know about the solution.

Thank you in advance,
Mandana

---

### Post by Iowan on 2008-02-25
Did you restart networking after the edit? (**/etc/init.d/networking restart**)
Also, when you do get an address on eth0, what is it?  IIRC, it can't/shouldn't be in the same subnet as ath0 (or other interface).

---


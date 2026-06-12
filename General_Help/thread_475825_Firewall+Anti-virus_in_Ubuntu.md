---
title: "Firewall+Anti-virus in Ubuntu"
date: 2007-06-16
forum: General Help
---

### Post by yay on 2007-06-16
Should I use a firewall or/and an anti-virus or is it useless? How can I be infected?

---

### Post by Shazaam on 2007-06-16
Iptables is your "firewall". You can install a GUI frontend for it if you need a simple way to configure iptables. There are many posts here that deal with iptables. As far as an anti-virus you don't really need one. There are some you can install if you feel the need.

---

### Post by thePsychologist on 2007-06-16
Ubuntu comes with a good firewall system called iptables. You can download some graphical managers to customize it. This is good if you want to do some things like port forwarding for BitTorrent clients. One is called "firestarter" (sudo aptitude install firestarter).

An antivirus is good if you're trading lots of things with Windows users so you can tell them if they sent you a virus, but virtually in all cases you cannot be infected by these viruses. There was a Linux viruses as a proof of concept but it isn't out there in the wild and won't affect you.

There was also a cross platform "virus" that ran through OpenOffice macros but, hey, anything like that can compromise any system. Good idea if you share lots of docs with MS users, try "sudo aptitude install clamav" which is a virus scanner. Most people don't bother.

---

### Post by floke on 2007-06-16
That's right. Iptables is an inbuilt firewall (firestarter is just the configuration GUI for it). And you really don't need AV unless swapping Windows files.

It takes a bit of time to get used to; but you really don't need this stuff anymore :D.

Try this to see how secure you are:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by yay on 2007-06-16
Thanks for the replys! I have no problems with portforwarding in bit torrent clients, and I haven't configured those "iptables", the only thing I did was opening a port in the router and the clients say everything is OK, so I think I don't need to change "iptables".

Thanks again ;)

---


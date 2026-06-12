---
title: "How do you connect to the internet using the live CD?"
date: 2005-07-03
forum: General Help
---

### Post by miSs017 on 2005-07-03
[FONT=Tahoma]I'm currently new in using Ubuntu and I used the live CD before installing. But I first of all I want to learn how to connect. Can someon please tell me how? I've tried the 'Networking Option' and when I tried using the help file it showed a screenshot different from the actual; so I can't understand. And it didn't prompt for a password. Can someone please help? Thanks.[/FONT]

---

### Post by miSs017 on 2005-07-03
Can someone please help?? I'm currently on a rush and I do need help immediately. Thanks.

---

### Post by crashtest on 2005-07-03
[QUOTE=miSs017]Can someone please help?? I'm currently on a rush and I do need help immediately. Thanks.[/QUOTE]

Look under System -> Administration -> Networking, then configure the interface.

---

### Post by miSs017 on 2005-07-03
[QUOTE=crashtest]Look under System -> Administration -> Networking, then configure the interface.[/QUOTE]

[FONT=Tahoma]Yes, I have tried that and configured it. But after that, isn't it that you have to activate it? Well, I did but when I close the window and open it again; it is deactivated. What's happening?[/FONT]

---

### Post by crashtest on 2005-07-03
[QUOTE=miSs017]Can someone please help?? I'm currently on a rush and I do need help immediately. Thanks.[/QUOTE]

Look under System -> Administration -> Networking, then configure the interface.

---

### Post by crashtest on 2005-07-04
> **miSs017][FONT=Tahoma]Yes, I have tried that and configured it. But after that, isn't it that you have to activate it? Well, I did but when I close the window and open it again said:**
> 

Are you trying to get an IP address by DHCP?  After activating the interface, check if you have received an IP.  In a terminal, type /sbin/ifconfig.  You should see something like:

boone@disorder:~$ /sbin/ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0F:F8:4D:48:06
          inet addr:192.168.2.118  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:f8ff:fe4d:4806/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:861919 errors:36673 dropped:0 overruns:0 frame:36673
          TX packets:672193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:41361 txqueuelen:1000
          RX bytes:1236433189 (1.1 GiB)  TX bytes:37484560 (35.7 MiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9539443 (9.0 MiB)  TX bytes:9539443 (9.0 MiB)

If DHCP is not working on your network, try entering a static address - assuming you know what the the proper parameters to enter:

-IP address, subnet mask, default gateway.  Also make sure you have a nameserver listed in /etc/resolv.conf.  On my system resolv.conf looks like this: nameserver 192.168.2.1

---

### Post by miSs017 on 2005-07-04
Not really. In fact I don't even understand what you said :smile: . Anyway, all I inputted was the user name, phone number, password, and the modem port(which I'm not sure if it's correct). Sorry, but I'm really a n00b when it comes to Linux.

---

### Post by crashtest on 2005-07-04
[QUOTE=miSs017]Not really. In fact I don't even understand what you said :smile: . Anyway, all I inputted was the user name, phone number, password, and the modem port(which I'm not sure if it's correct). Sorry, but I'm really a n00b when it comes to Linux.[/QUOTE]

So I guess you're trying to configure dial-up networking with a modem?  Or do you have a broadband connection like cable, and a router?  Are there other computers on your network, or is this the only one?

---

### Post by miSs017 on 2005-07-04
I'm configuring a dial up modem and I don't have a network.

---

### Post by crashtest on 2005-07-04
[QUOTE=miSs017]I'm configuring a dial up modem and I don't have a network.[/QUOTE]

I'm afraid I can't help you then.  You said you are not sure what port the modem is on?  I think you'll need to solve that first.  Hopefully someone else can jump in here with some help for you.  Good luck.

---

### Post by miSs017 on 2005-07-04
Ok, sorry for bothering you. Anyway thanks for trying to help.

---

### Post by crashtest on 2005-07-04
[QUOTE=miSs017]Ok, sorry for bothering you. Anyway thanks for trying to help.[/QUOTE]

No bother at all, I just don't have any experience using Linux with dial-up.  It should be straight forward, but I don't want to give you any false information.

If no one else answers, I would start a new thread with "how do I configure dial-up networking using the live cd?" as the subject line.

---

### Post by miSs017 on 2005-07-04
Ok, thanks again. I'll just wait til someone helps.

---


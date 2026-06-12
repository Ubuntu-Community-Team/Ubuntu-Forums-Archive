---
title: "Internet Problem"
date: 2007-01-02
forum: General Help
---

### Post by kusal on 2007-01-02
I Just installed ubuntu 5.10 in my computer. 

I have a ADSL connection and i have three computers in my home  so i use a ADSL router to give all three machines internet, when i boot my computer with ubuntu i can't access internet from firefox.
but in windows as soon as i open IE the internet is there.

pls help

thnx :-D

---

### Post by NGEvo on 2007-01-02
I have same problem :confused:

---

### Post by scrooge_74 on 2007-01-02
> **kusal said:**
> I Just installed ubuntu 5.10 in my computer. 

I have a ADSL connection and i have three computers in my home  so i use a ADSL router to give all three machines internet, when i boot my computer with ubuntu i can't access internet from firefox.
but in windows as soon as i open IE the internet is there.

pls help

thnx :-D

You mean you installed ver 6.10?

From a command line try sudo ifconfig andd post back the info

does your router is using DHCP to assign IP addresses?

do sudo ifdown eth0 (assuming eth0 is been recognize from sudo ifconfig as your ethernet card)
sudo ifup eth0
sudo dhclient eth0

---

### Post by mkent91 on 2007-01-02
scrooge_74 I'm going to give you a list of things to do.

1) Open Firefox in Ubuntu
2) Type in "about:config" as a address
3) In filter type in "iPv6"
4) If "network.dns.disableIPv6" is not set to true.(bold print)
5) If not, then double click on it to set the value to true.



if this doesn't work for you I'm very sorry....and I don't know what the problem is.

---

### Post by kusal on 2007-01-02
> **scrooge_74 said:**
> You mean you installed ver 6.10?

From a command line try sudo ifconfig andd post back the info

does your router is using DHCP to assign IP addresses?

do sudo ifdown eth0 (assuming eth0 is been recognize from sudo ifconfig as your ethernet card)
sudo ifup eth0
sudo dhclient eth0

No it's 5.10 i know its a late version.

i think ubuntu dose'nt  detect my network card when i type in the second line of command it say that interface is not configured.
and when i check it on device manager, there was no detected network cards

can i do anything about this
thnx

---

### Post by scrooge_74 on 2007-01-03
You should try a newer version it will probably detect your hardware better

---


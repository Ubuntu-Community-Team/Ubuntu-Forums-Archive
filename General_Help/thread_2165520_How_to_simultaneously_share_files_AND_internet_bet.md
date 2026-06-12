---
title: "How to simultaneously share files AND internet between two ubuntu machines?"
date: 2013-08-05
forum: General Help
---

### Post by community on 2013-08-05
I used to share wired internet connection from one machine to other via hotspot. And I managed to share files by creating an ad-hoc network by assigning ip address. But failed when tried to do both simultaneously. Can anybody suggest a method for doing both? I have two ubuntu machines. One with wired internet connection and other doesn't. I need to share this internet connection with other. Along with that I must be able to share files between the two, please...

---

### Post by BBQdave on 2013-08-05
I use [**vsftpd**]("https://security.appspot.com/vsftpd.html") and [**FileZilla**]("https://filezilla-project.org/") to share files :)

To share internet connection, I think the easiest most flexible option - Internet Router with firewall. A layer of protection for the machines on your network, and an easy way to have multiple machines access the internet.

---

### Post by community on 2013-08-06
You mean an external router? If so, why should I need a solution. I know it is possible to do both without the help of any other device. Can anybody help me?

---

### Post by Rsxhawk on 2013-08-06
I've never set up an Ad Hoc network before but with the setup you're proposing, Ubuntu would need something like Windows ICS (internet connection sharing) enabled.  I don't know anyone who has ever set up a connection successfully like that either and I'm not sure Ubuntu can do it.  Doing both ad hoc and sharing an internet connection doesn't sound possible as the machine with the internet connection would take preference for the wired connection over the wireless adaptor.  You say you got it to work before, was that also on Ubuntu?  You say you got ad hoc mode working by "simply assigning an ip address to it"....what IP did you assign?  Were both Wireless adaptors on the same sub-network?  Since I'm reading that AD HOC is mostly layer 2, it would then follow that if you assigned an IP address to the wireless clients that were in the same sub network, then they would be able to talk to each other, but then getting that traffic out to the internet via a wired interface, I'm not so sure about.

BBQdave is right, the easiest solution would be to just go get a cheap linksys/d-link/netgear wireless router, set up an SSID with encryption to connect both your wireless clients to - they will get an "internal" ip address from the router, and then the router will NAT everything out to the internet.  I would suggest reading up on the basics of NAT and how it all works.  AD HOC wouldn't be my first choice as I'm not even sure you can even dictate what type of wireless encryption that would be used over such a link.

---

### Post by community on 2013-08-08
Rsxhawk, I just made an ad-hoc network with address 192.168.1.1, subnet 255.255.255.0 and gateway as 0.0.0.0 on one machine and 192.168.1.2 as address on another (remaining same) and I was able to share files easily. I was eager to know whether wired internet connection can also be shared in a similar way along with file sharing, that's all. One question: Whether files can be shared through hotspot? Because wired internet connections are normally shared by putting up a hotspot. I think users connected to hotspot can access files from the machine having wired internet connection. Whether reverse is possible? You got me, right?

---

### Post by SlugSlug on 2013-08-08
well the gateway on the wired pc should be your modem / router and I think the gateway on the other PC should be the main PC's IP

---

### Post by community on 2013-08-08
HOTSPOT worked. Thanks to all. I just made the wired internet connection available to the other by just clicking 'Use as Hotspot'. Surprisingly I was able to transfer files between the two easily. Once again thanks to all. HOTSPOT is the man!!!

---

### Post by Rsxhawk on 2013-08-09
Glad to hear it.  I did a quick search for ubuntu hotspot and I found the following article about it.  Pretty slick, I didn't know Ubuntu could do that.....the only bad part I see is that for the AD HOC connection that is made between wireless clients, the only encryption available is WEP, unless that's been updated since the writing of that article.  

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

---


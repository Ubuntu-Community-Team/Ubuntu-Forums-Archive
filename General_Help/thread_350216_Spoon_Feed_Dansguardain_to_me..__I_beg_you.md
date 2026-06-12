---
title: "Spoon Feed Dansguardain to me..  I beg you"
date: 2007-01-31
forum: General Help
---

### Post by Zephirus on 2007-01-31
Hello everyone, I have use ubuntu beofore and I am able to isntall the standard version as well as the server version with no problem...

I just need help installing and setting up dans guardain.    I have been to their website and went through the howto but even it was too difficult and confusing.   I don't know much about linux but I have seen dans guardian work in the past and it is the perfect solution to the situation I have.   

So... lets say I install a lamp server just so there is no GUI (scares people off).   Or maybe its easier with the GUI to get it working... 

Tell me what to do step by step....


Keep in mind that i have 2 network cards in this computer and going to each workstation and chaning anything would be near impossible.    I need to drop this in and forget about it.   I dont want to change anything on the user computers because we have a few hundred of them...     


Ultimatly I want to put this in our network between the lan and the gateway to filter out porn and such.   I understand how networks work so there is no need to go into a IP address lesson.    I have 2 network cards in this computer.   The first I am going to set as the LAN Gateway, and the other I will have on a different network along with the DSL router.   

If anyone would help, Id really appreciate it.   Email works for me too if you want to do it that way.   [email]cyohn@fannincountyga.org[/email]      

Thank you for your time.

---

### Post by dad311 on 2007-01-31
First install squid:

1)    sudo apt-get install squid
2)    Fix squid.conf file.  The "visible_hostname" will need to be configured and the /etc/hosts file updated.

Here is an example of the "visible_hostname" and /etc/hosts file.

FROM /etc/squid/squid.conf
visible_hostname Ubuntu-Server

FROM /etc/hosts
127.0.0.1 localhost
192.168.1.27 Ubuntu-Server

3)  sudo /etc/init.d/squid start
Make sure squid starts

4) sudo apt-get install dansguardian
Edit /etc/dansguadian/dansguardian.conf
Change line UNCONFIGURED to #UNCONFIGURED

5) /etc/init.d/dansguardian start

---

### Post by Zephirus on 2007-01-31
Ok but once I have that, how do I adminstrate it?    How do I tell ubuntu to accept all net traffic coming in on port 80 on the LAN card, and send it out on port 80 on the WAN card?    I can not change any proxy information on the cleint comuters cause we have 500 of them... thats not feasible.   

I dont want to touch the cleint computers.  I want to drop this box in place, give the LAN network card the current default gateway's IP address, and let dans filter everything that comes in, and then send it out the other network card to our ISP router.

---

### Post by dad311 on 2007-01-31
I believe you want a transparent proxy server.

checkout [http://nyetwork.org/wiki/DansGuardian](http://nyetwork.org/wiki/DansGuardian)

---


---
title: "access to PC with dynamic IP"
date: 2013-01-14
forum: General Help
---

### Post by marchelloUA on 2013-01-14
Hi all, 

my need is to access my home computer (kubuntu, dynamic IP) from office (windows xp). 

As far as I know, I should use some windows client like putty, but what about dynamic IP ?

---

### Post by I8NY on 2013-01-14
So you want to remote PC to your home pc from your office.  If this office is in your house then you can just find the dymnamic IP of the Kubuntu PC by the MAC address by typing in, "sudo nmap -sP 192.168.0.0/24"  Find the Kubuntu MAC address in the list and it should show the IP it is using.  Really you should use static IP address if you are hardwired.  If the office is connecting over the internet and you have a dynamic public IP then you will have to write down the public IP at home and hope it doesn't change by the time you try connecting.   Also you have to have port-forwarding to allow inbound connection from the internet or else it won't work.

---

### Post by marchelloUA on 2013-01-14
[I8NY]("http://ubuntuforums.org/member.php?u=862563"),
My home pc is connected via wi-fi router.
Wi-fi router gets external dynamic IP from ISP via DHCP, so it can change several times a day. 

I hope I can use some easier method than "hope it doesn't change by the time you try connecting".

---

### Post by d4rk0wl on 2013-01-14
What is the protocal you are looking to use? VNC, SSH ect.

You could always look into registering a domain name and then using ddclient and zonedit to automaticaly resolve DNS to the updated IP whenever it happens.

Regards,
- D4rk0wl

---

### Post by marchelloUA on 2013-01-14
[d4rk0wl]("http://ubuntuforums.org/member.php?u=1767387"), 

I'm about to use SSH protocol. Well, sure I'd like also to see remote X window, but not sured it is possible at all in my situation (under windows XP in office). 

Could you please give me example of "look into registering a domain name and then using ddclient and zonedit to automaticaly resolve DNS to the updated IP" ?

---

### Post by d4rk0wl on 2013-01-14
> **marchelloUA said:**
> 
Could you please give me example of "look into registering a domain name and then using ddclient and zonedit to automaticaly resolve DNS to the updated IP" ?

ddclient is a daemon process (it runs in the background) which checks a site that tells you your current IP address (i.e. ipchicken.com) every 10 min or so, if it notices that your IP is different, it'll update the DNS server for your domain name (i.e. zoneedit).

In a nutshell, zoneedit is a free DNS service which says.. hey you know the address [www.[domain].com?](www.[domain].com?) Yeah, well that is actually this [IP Adress] and points the connection to the IP address, you can read all about it [here]("http://sourceforge.net/apps/trac/ddclient/")

Regards,
- D4rk0wl

---


---
title: "Apache2 only works locally on VMWare host"
date: 2013-11-24
forum: General Help
---

### Post by michael86 on 2013-11-24
I am new to the forum, consider ms a casual Linux user, I am a strong in networking with a primary background in Windows...
Here's my problem. I have a new install of Ubuntu 12.04 Desktop in VM Player, the NIC is set to bridged and replicate physical environment. I have changed the /etc/hostname a fqdn (apache.mydomain.local). I registered an A record on my windows server for this and can ping the fqdn no problem. I am not blocking port 80 on my LAN. I am listening on port 80, allow all and the ufw (firewall) is inactive.
I can browse to the default apache2 test web site on the localhost just fine. [http://localhost](http://localhost), [http://apache.mydomain.local](http://apache.mydomain.local), and [http://192.168.0.xx](http://192.168.0.xx), where xx is the local IP address all work fine on the localhost in Firefox.
When I attempt to browse to it from any other computer on my LAN, I get "The page cannot be displayed". I get no entries in the apache logs. What am I missing here? Something with the apache2 configuration?
Thanks in advance.

---

### Post by Doug S on 2013-11-24
Hi and welcome to Ubuntu forums.

With a default installation of the apache web server on 12.04, it should work fine. I'm not sure what to suggest, but myself I would use a packet sniffer (tcpdump or wireshark) to observe if the port 80 packets are arriving at the VM computer.```
sudo tcpdump -n -tttt -i eth0 port 80
```(Replace "eth0" with your interface name.)

---

### Post by michael86 on 2013-11-24
Thank you for the suggestion. I wasn't getting anything at all so that led me to believe it was simply a layer 3 issue. Most of my testing was from the VM host computer, not sure if routing was goofed or what. I set a DHCP reservation on my server and tested connectivity from there and it was fine. The VM host is Windows 8.1 so who knows what the heck was going on. I appreciate the response.

---


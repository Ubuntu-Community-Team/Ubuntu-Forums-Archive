---
title: "Network problem"
date: 2004-11-19
forum: General Help
---

### Post by Arnb on 2004-11-19
Setup eth0 using System configuration --> Network
Attempting to connect via laptop pcmcia 10/100 card works only on rare occasions. Usually the check box unchecks itself within a second using manual or auto dhcp. Is there any place or command that can be used to find out what is failing?

---

### Post by az on 2004-11-19
sudo ifconfig
sudo ifup eth0
sudo ifdown eth0
sudo tail -f /var/log/messages


Many other things, too.

---

### Post by Arnb on 2004-11-19
Thanx azz that got it to work, but it still won't work using standard Ubuntu Networking control at boot, the check box disappears and won't connect even though the first ifup says the network is active.

The root console follows below, hopfully someone can figure out what's going wrong. There are errors about a sit0 unknown hardware address type 776 and wireless which I don't have. 

TIA
Arn

root@Mine:/home/aab # ifup eth0
ifup: interface eth0 already configured
root@Mine:/home/aab # ifdown eth0
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:xxxxxxxxxxxxxxxx
Sending on   LPF/eth0/00:xxxxxxxxxxxxxxxxx
Sending on   Socket/fallback
DHCPRELEASE on eth0 to xxx.xxx.xxx.xxx port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
root@Mine:/home/aab # ifup eth0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:xxxxxxxxxxxxx
Sending on   LPF/eth0/00:xxxxxxxxxxxxx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
ip length 328 disagrees with bytes received 332.
accepting packet with data after udp payload.
DHCPOFFER from 10.95.128.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 328 disagrees with bytes received 332.
accepting packet with data after udp payload.
DHCPACK from 10.95.128.1
bound to xx.xxx.xxx.xxx -- renewal in 1366 seconds.

---

### Post by Arnb on 2004-11-19
I think I found the answer on
[http://www.ibiblio.org/mdw/HOWTO/DHCP/x74.html#TROUBLESHOOTING](http://www.ibiblio.org/mdw/HOWTO/DHCP/x74.html#TROUBLESHOOTING)
I've been swapping the network card between my Win Xp machine and the Ubuntu machine.

3.10.7. I have followed all the steps but still my machine is not able to connect

The cable modem will usually memorize the ethernet address of your network card so if you connect a new computer or switch network cards you will somehow have to "teach" your cable modem to recognize the new computer/card. Usually you can turn of the modem and bring it back up while computer is on or you will have to call tech support and tell them that you have changed a network card in the computer. 

Update: Reset and restarted the cable modem, problem remains  ](*,)

---

### Post by arctic on 2004-11-19
i has a similar problem, that is my connection was gone after differing periods of "net-connection". i solved it the following way:

in case you are you able to ping any site for a "longer time" (that is: enough time for downloading one of the following packages at a time), try to ping your ubuntu mirrors in one terminal and run in a second terminal 
sudo apt-get install resolvconf
sudo apt-get install pump
sudo apt-get install dnsmasq

this will replace your dhcp with pump. it worked on my box extremely well.

---

### Post by Arnb on 2004-11-19
Artic
I do appreciate your fix to this problem, but at this point I've had about enough modifications, changes and patches to a product that is supposed to be a "slamdunk" desktop Linux install.

While I did not expect perfection, I've had to perform work arounds for:
Dialup Networking
10/100 Networking
NPT
Installing Firefox 1.0
IPV6 
plus a couple of other things that are still outstanding on my machine.

While this may seem trivial to most seasoned Linux users, I *was* a rank Linux noobie-beginner  :roll: user just four days ago and just don't feel like diving deeper into Linux parts bin at the moment.

---

### Post by arctic on 2004-11-19
well, installing the files i mentioned is not a big thing to make. the problem you are encountering is the one i have encountered with nearly every 2.6 kernel based distro so far. and kernel.org already admitted that there is a bloody bug in the kernel that has to do with ipv6 and which will be solved (hopefully) finally when kernel 2.6.10 is out (2.6.9 is already working in a good way). installing the above mentioned files via synaptic is way easier than hacking the files manually (which is the "dirty" alternative).

---


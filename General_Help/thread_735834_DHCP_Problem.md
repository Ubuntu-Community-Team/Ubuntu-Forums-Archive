---
title: "DHCP Problem"
date: 2008-03-26
forum: General Help
---

### Post by akks on 2008-03-26
Hi All,
 Am a newbie to Linux s and recently found my intrest budding in Networking. So trying to learn all the concepts Apache, DNS etc. There was a problem at office recenty with DHCP which has caught me confused. Here is the problem:
 
Our LAN at office is set up using DHCP. Recently one morning none of us at office were able to login. The reason we found was, we were not getting the correct IP addresses. The DHCP was set to lease LAN addresses (192.168.x.x).   So i tried to manually set  IP on my laptop using ifconfig (i.e. ifconfig  eth0  192.168.1.28). Although i was able to ping the lan ( 192.168.1.x). When i tried to ping google.com, i got and error "connect: network is down". I cant give you much details about the LAN set up at office but i am sure the the same machine on which DHCP runs also acts as the gateway. 

My question is : if i can ping the LAN, why cant i connect to the internet. Because with DHCP also i used to get the same address 192.168.1.28. I am missing something about DHCP?. I am totally confused. Can you tell me where i am understanding wrong?

Ah, and we use Linux desktops in office( REdhat, SUSE and Ubuntu). But that should not matter for DHCP, is it?

---

### Post by SpaceTeddy on 2008-03-26
a connection to a network which is directly attached to a network card only requires the network card to have an IP address within the same range as the rest of the network. i.e. if you give yourself the IP 192.168.1.2 and the subnetmask 255.255.255.0 you will automaticially be able connect to any computer that is in the segement as you, so having an ip like 192.168.1.x and the same subnetmask

however, this only applies for LANS with no routers inbetween. in order to connect to other Lans (and ultimativly the internet) you need to tell your computer where to find it. this is what routes are for. The most general rule of all is the default gateway. Anything that cannot be found in a network attached to your network cards will be sent to it in hope that the default gateway knows what to do with it. In general, the default gateway is the computer between you and the internet.

so set the default gateway on an ubuntu box, run this command:
```
sudo route add default gw 192.168.1.1
```
where the ip has to be the one from the computer connecting anyone to the internet.

This will give you reachablitly to the internet. However, one important thing is still missing - DNS. DNS is for changing names into ip-addresses. Without it, you could only access servers by their ips, and i bet you do not know the ip of google :)

the the last thing you need to set is the dns server. They are set in /etc/resolv.conf. There should be an entry there called "nameserver" one or multiple times. there has to be at least one ip, so that your computer can ask a dns server what ip google.de is.

so, in general, you need three things on a client to connect to the internet (these are usually all pushed by a DHCP server)

1.) an IP-Address
2.) a default gateway
3.) one or more DNS servers

hope you can make some sense from this :)

---

### Post by akks on 2008-03-26
Thanks SpaceTeddy,
 I spent 3 hours yesterday night googling about DHCP (gosh! should have read your reply). That solved most of my problem. Now i get it. Thanks again. And by the way if you know any good online tutorials for DHCP please let me know.  I am trying to configure DHCP at my home now. :)

---

### Post by SpaceTeddy on 2008-03-26
read step "configunring the client" [here]("http://ubuntuforums.org/showthread.php?t=713874"). it describes the most simple setup of dhcp and dns server for internet connections... of course, you can then start from there.

hope it helps :)

---


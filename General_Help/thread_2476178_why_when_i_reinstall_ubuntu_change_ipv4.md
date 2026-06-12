---
title: "why when i reinstall ubuntu change ipv4"
date: 2022-06-19
forum: General Help
---

### Post by chat-4432 on 2022-06-19
when i reinstall ubuntu ipv4 has change last two digit from 70 to 71 ???
that course me econrefuse when i try to connect my web server.

---

### Post by HermanAB on 2022-06-19
If you want a static IP address, set it in the DHCP server in your router device.

---

### Post by ActionParsnip on 2022-06-19
That's how DHCP works. You can set a static IP if you need this but if the system isn't a server of any kind then it doesn't matter

---

### Post by mIk3_08 on 2022-06-19
> **chat-4432 said:**
> when i reinstall ubuntu ipv4 has change last two digit from 70 to 71 ???
that course me econrefuse when i try to connect my web server.
> **HermanAB said:**
> If you want a static IP address, set it in the DHCP server in your router device.
I agree with HermanAB you can set static IP in your local router. Other local router also uses mac address to specify the device which you will give the specific static IP address. Regards and cheers.

---

### Post by TheFu on 2022-06-19
I disagree with using DHCP to force static IPs for systems that don't move.  When the DHCP server is down and you reboot any other system that only gets IPs from DHCP, those will all be stupid IPs resulting, not what you want.

Manually setup static IPs inside the system.  Do it for servers and desktops.  An argument can be made for IoT devices, phones, tablets and laptops to use the DHCP Reservation method, but understand the limitation and risk.

I don't want my systems to fail and be put on some 169.x.x.x subnet just because a DHCP server isn't working.

---

### Post by ActionParsnip on 2022-06-19
What are you getting DHCP from if the DHCP server is down? If this is down then that issue should be attended rather than simply working around it with static IPs which are an administrative nightmare

---

### Post by TheFu on 2022-06-19
> **ActionParsnip said:**
> What are you getting DHCP from if the DHCP server is down? If this is down then that issue should be attended rather than simply working around it with static IPs which are an administrative nightmare

Desktops and servers don't use DHCP here.  They are locally configured on each system.  

In a house with just laptops, then dhcp reservations are the most reasonable answer.

---

### Post by TheFu on 2022-06-19
double-post ... sorry.

---

### Post by chat-4432 on 2022-06-20
> **HermanAB said:**
> If you want a static IP address, set it in the DHCP server in your router device.
[https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet)
what is subnet is that matter ?
what is default gateway is it 192.168.1.1 ?  how to find it ?
which dns server should i use  ?

---

### Post by TheFu on 2022-06-21
> **chat-4432 said:**
> [https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#3-wifi-or-ethernet)
what is subnet is that matter ?
what is default gateway is it 192.168.1.1 ?  how to find it ?
which dns server should i use  ?

Yes, the subnet matters.  It needs to be the same subnet that your router is setup to provide (almost always).  **ip addr** will show the current IP and subnet. You just need to know how to read it.

Default gateway can be different on different networks.  The routing table show it.  **route -n** will show it.  Or **ip route** which does too, but it uglier.

Which DNS should you use?  There are thousands of them in the world. It is an opinion choice.  If you have kids, you might want DNS to filter adult content addresses.  If you want the absolute truth for all websites in the world, there are some choices.  A slow DNS can make the entire system free slow.  However, the DNS provider does see every domain lookup your computer requests, so there may be some privacy considerations.

Examples from one of my systems, but most definitely will not be used by your network:  Run the same commands, look at the highlighed text in my example and find that in your output to get the answer:

IP address and Subnet:
```
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 52:54:00:1d:4c:e5 brd ff:ff:ff:ff:ff:ff
    inet **172.22.22.3/24** brd 172.22.22.255 scope global ens3
       valid_lft forever preferred_lft forever
```
IP = 172.22.22.3
subnet = 172.22.22.0/24 ---> a netmask of 255.255.255.0  

```
$ ip route
default via **172.22.22.1** dev ens3 proto static 
172.22.22.0/24 dev ens3 proto kernel scope link src 172.22.22.3 

```
Default gateway is: 172.22.22.1

For DNS, the fastest servers tend to be either Google's DNS or Cloudflare's DNS.  Google is all about spying, but they claim they don't. They've been caught lying on other privacy issues. 8.8.8.8 and 8.4.4.8 I think.  I don't use google.

Cloudflare is owned by a man who believes strongly in freedom of speech, absolutely, sometimes so much that 80% of the world thinks he's evil. 1.1.1.1 and 1.0.0.1. This is where I point my DNS.

There are a number of DNS filter services available, some free, some at a small annual price.  They have categories of things to be filtered. Violence, sex, religious stuff, so parents and people who don't want to see content they could find objectionable can be filtered from access. OpenDNS is one. Oddly, to find the IPs, you have to already have a DNS setup. ;)  

There are tools that we can run on our computers, over our internet connection, which will speed test hundreds of different DNS servers and provide a list back to choose from.  A web search will find these tools and more information.

A slow DNS is definitely bad.  For any Unix-based OS, lots of things require DNS lookups.  By default, ubuntu runs a caching DNS on every system using systemd-resolved (in recent releases).  When you make settings in the Ubuntu network GUI, it should be changing where systemd-resolved points for DNS, but the system should still have a local caching DNS too.  I don't use this method for some complex reasons, but you probably should, unless you have 5+ computers on the LAN. then I'd suggest running a LAN DNS server, let it perform all the caching and remove the systemd-resolved subsystem from the computers there.  However, based on the questions asked (networking skill level), this would be a bad idea.

---

### Post by chat-4432 on 2022-07-21
i think method of DHCP is slow [https://www.makeuseof.com/raspberry-pi-set-static-ip/](https://www.makeuseof.com/raspberry-pi-set-static-ip/)
how can i config using single command or config file before boot on my pc ??

---

### Post by TheFu on 2022-07-21
Ubuntu computers (x86-64) have static IPs configured in multiple different ways. If you are running a desktop, google for "static IP ubuntu desktop guide"

Change "ubuntu" for the distro you are running.  Lubuntu, Xubuntu, Mate, etc.... to see the instructions for your flavor.
Servers are different.

I've never seen nor used Ubuntu on a raspberry pi. I have setup static IPs on mine, but they use specialized distros for the purpose. Setting static IPs on them was achieved by following the instructions for those distros.

---


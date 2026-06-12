---
title: "Ubuntu homemade router iptables issues"
date: 2018-06-24
forum: General Help
---

### Post by lda4526 on 2018-06-24
[COLOR=#1A1A1A][FONT=&quot]I was running 18.04 on my odroid xu4 and I was having configuration issues due to 18.04 using netplan. I dd'ed another sd card with 16.04 and gave it another go. I am no longer having those issues and my DHCP server is running like a champ and issuing IP addresses to anything that connects to it. Unfortunately, I am having issues configuring Iptables correctly and would appreciate some help! I am 99.9% sure that it i just an iptables issue as my Linksys router that I connected to it gets an ip address, dns servers, etc correctly.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]Here are my rules: [https://pastebin.com/L4p2zxFK](https://pastebin.com/L4p2zxFK)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]Eth0 is my internal LAN and eth1 is my WAN. I have ip6tables rules in the pastebin but they are pretty standard and I did not include any routing features as I would prefer to only have this be an ipv4 (If that is possible?).[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]Any help would be appreciated![/FONT][/COLOR]

---

### Post by Doug S on 2018-06-24
First, suggest to get rid of any ipV6. I just boot with ipv6 disabled, with this on the grub command line (in /etc/default/grub):

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```

Second, I think you have eth1 and eth0 reversed on two of your lines. Suggest this:

```
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT-o lo -j ACCEPT
sudo iptables -I INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sudo iptables -A FORWARD -i [COLOR="#FF0000"]eth1[/COLOR] -o [COLOR="#FF0000"]eth0[/COLOR] -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i [COLOR="#FF0000"]eth0[/COLOR] -o [COLOR="#FF0000"]eth1[/COLOR] -j ACCEPT
```
With a default policy of ACCEPT, this line actually isn't needed:```
sudo iptables -A OUTPUT-o lo -j ACCEPT
```

---

### Post by lda4526 on 2018-06-25
Thank you for the reply! It was very helpful and informative. Your Iptables configuration worked and I now have a fully functional router. I even have ipv6 disabled by default now, so I get no dns leaks when connecting to a VPN now(The VPN provider does not have ipv6 support server side).

```
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT-o lo -j ACCEPT
sudo iptables -I INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sudo iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

I had to add this to my /etc/sysctl.conf file.

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

The part about adding the ipv6 disable did not work on my x64 based computer with grub, and did not work on my odroid either when I added it to the boot ini file.

You think its possible to set up DNS over TLS using Unbound on this setup or do you think I should try it on a different client? I was thinking that it may interfere with my dhcp server if I installed it on the router. I was looking at this guide: [http://blog.thestateofme.com/2018/04/04/howto-secure-your-dns-with-a-raspberry-pi-unbound-and-cloudflare-1-1-1-1/](http://blog.thestateofme.com/2018/04/04/howto-secure-your-dns-with-a-raspberry-pi-unbound-and-cloudflare-1-1-1-1/)

---

### Post by SeijiSensei on 2018-06-25
> **lda4526 said:**
> You think its possible to set up DNS over TLS using Unbound on this setup or do you think I should try it on a different client? 

Why not just install BIND on the router and use it as a caching nameserver for all the clients?  If you use isc-dhcp-server on the router, you can create an interface between the two so that client hosts are added to the nameserver records when they make DHCP requests.

---

### Post by lda4526 on 2018-06-27
I found this guide using unbound: [http://blog.thestateofme.com/2018/04/04/howto-secure-your-dns-with-a-raspberry-pi-unbound-and-cloudflare-1-1-1-1/](http://blog.thestateofme.com/2018/04/04/howto-secure-your-dns-with-a-raspberry-pi-unbound-and-cloudflare-1-1-1-1/). Did not find much for the program you were referencing. As I am definitely not an expert, I was thinking about trying unbound first. In addition, I was also thinking about installing pi-hole on another device within my network anyway, so I figured I could do both on that piece of equipment. I am not sure about installing pi-hole though, as they have no ppa or gpg verification, and I typically do not run software that I cannot verify.

---

### Post by 1clue on 2018-06-27
Why get rid of ipv6? Or was that just an intermediate step to get ipv4 working?

Yes, it's more complicated managing a dual stack router, but I see no real reason not to do so.

---

### Post by Doug S on 2018-06-27
> **1clue said:**
> Why get rid of ipv6? Or was that just an intermediate step to get ipv4 working?

Yes, it's more complicated managing a dual stack router, but I see no real reason not to do so.for my part of it, the OP said he didn't want IPV6, so I told him what I do. I have a very complicated iptables rule set for my Ubuntu server that acts as my main router/DNS/DHCP, and I simply have not bothered to learn about, or include, IPV6 yet.

---

### Post by 1clue on 2018-06-27
> **Doug S said:**
> for my part of it, the OP said he didn't want IPV6, so I told him what I do.


I missed that part.

> 
I have a very complicated iptables rule set for my Ubuntu server that acts as my main router/DNS/DHCP, and I simply have not bothered to learn about, or include, IPV6 yet.

With respect to the core fundamentals (ip addresses, netmasks, routing) it's exactly the same but with more bits. Link-local and such is a bit of a curve, but you don't need dhcp. Your dns already supports ipv6 if you just use it.

I have ipv6 enabled but not much more because my isp doesn't support static ipv6 addresses. I can of course use link-local and such internally, but nothing global.

The key thing, when you get to it, is that you can block a nic's ipv4 address and the ipv6 address will still be accessible, and vice versa. The same is true for 2 ipv4 addresses on the same nic.

---


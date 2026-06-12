---
title: "Voip"
date: 2015-09-29
forum: General Help
---

### Post by bogjumper on 2015-09-29
Good Day

I have used Ubuntu for the last 5 or more years but on and on/off type of use. I started using pcs back in Dos 3
and am reasonably capable. Having used DOS commands back in those days it was still nice to get GUI altho
even today I still use the odd command line.When I started using  Linux I was in my late 60s and this is why I am writing
this opening comment.I have just installed 15.10 2. I am very pleased with it and its running well. In fact I have been toying with going to Win10
download but now am strongly thinking I will use Ubuntu for my outside dealings and keep my |XP/Win7 for other use.
I am not happy with Skype and looking around for an alternative came across Jitsi which looked good.
However it is not in the Ubuntu Store and I have failed to install. Is there any way we could get this University driven application to be included
to make installation easier.  [https://jitsi.org/Main/HomePage](https://jitsi.org/Main/HomePage). My apologies for taking so long and thanks for your patience.

---

### Post by grahammechanical on 2015-09-29
First of all there is not a Ubuntu 15.10.2 version and there never will be. There will soon be a 15.10 version but it will never get a point 1 release let alone a point 2 release because it on has 9 months support. Now I have no objection to running the Ubuntu 15.10 pre-release development version. I have been using it as my daily OS since development started in the last week of April. But I would recommend installing something like jitsi on Ubuntu 14.04 or 15.04 because there may not yet be a version for Ubuntu 15.10.

Other than that, the web site seems to make it easy to install

[https://jitsi.org/Main/DebianRepository](https://jitsi.org/Main/DebianRepository)

What specific problems were you having?

Regards.

---

### Post by ian-weisser on 2015-09-29
> **bogjumper said:**
> I have failed to install

Please elaborate. What have you tried? What was the failure?

Jitsi does produce Debian/Ubuntu packages. See [https://jitsi.org/Main/Download](https://jitsi.org/Main/Download)

There are two ways to add Jitsi to the Ubuntu Software Center:
The preferred way is for a volunteer (like you) to contribute the package to Debian, and then to stick around for a few years as a liason (packaging new versions, upstreaming bugs, etc). The package in Debian will automatically sync into the next release of Ubuntu. This way will ensure the highest-quality package and the widest availability. A good volunteer Debian Maintainer eliminates the need for Jitsi to produce and host their own packages, *and* gets them wider distribution and greater visibility.
(It doesn't need to be *you* - any Jitsi enthusiast can do it...or any member of the Jitsi project.)

The other way is for Jitsi to sign a Partnership Agreement with Canonical. Volunteers, obviously, can't do that.

---

### Post by bogjumper on 2015-09-30
My Thanks to both people who replied. I have this am discovered a video which gave me the right information and distros.
I am using 
[h=3][Ubuntu Desktop Next 15.10 (Wily Werewolf) Daily Build]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCEQFjAAahUKEwiK_YKY4J7IAhVMWBoKHa4RA7o&url=http%3A%2F%2Fcdimage.ubuntu.com%2Fubuntu-desktop-next%2Fdaily-live%2Fcurrent%2F&usg=AFQjCNHlHmDdsVk7_OGMWJA7N6qMWv16bA&sig2=ZYaWDBPpbdp-NW15HcYZ2A&cad=rja")[/h]which as I said I found very good. On an aside in windows XP I tried to download  a 2012 Skype package as I do not like this new version at all. I was surprised to see how many people feel the same. Regrettably Skype (Microsoft)are killing the old versions so its new or nothing. That is why I was exporing Jitsi . Im afarid I have got to a stage in life where I just want things to download and work without requiring the use of a 12 year old. So thanks for your advice.

---

### Post by arsaraiva on 2016-08-20
Good afternoon friends, I am facing a problem between the VOIP (SIP) and IPTables.
What  is happening is that when I run the client application VOIP  (already  tested the Twinkle and Zoiper), it can record the service and  when I  send to call any number, he gets the call and is calling (for a  time),  even if this number meets. At the same time it initiates the  call he drops the network such that only by resetting the router. I   know it's related to the firewall when it released the INPUT, OUTPUT in   iptables (iptables -P INPUT ACCEPT) he came to work, but falls into the   mistake of giving iptables -F and -X, lost all settings and the   application returned with the same problem, but now even I doing INPUT  and OUTPUT ACCEPT does not work.

Currently my iptables is like this:

#! / Bin / bash
####################
# # Cleaning tables
####################
iptables -F &&
iptables -X &&
iptables -Z &&
iptables -F INPUT &&
iptables -F OUTPUT &&
iptables -F FORWARD &&
iptables -F -t nat POSTROUTING &&
iptables -F PREROUTING -t nat &&
iptables -t nat -F &&
iptables -t nat && -X
iptables -F -t nat &&

######################
# Initialize modules #
######################
modprobe iptable_nat
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
modprobe ipt_LOG
modprobe ipt_REJECT
modprobe ipt_MASQUERADE
modprobe ip_tables
modprobe iptable_filter
modprobe nf_conntrack_ipv4
modprobe nf_nat_pptp
modprobe nf_conntrack_pptp
modprobe ip_gre
modprobe ppdev
modprobe ppp_generic
modprobe PPPoATM
modprobe ppp_async
modprobe ppp_deflate

####################################
# Freeing up internal network access #
####################################
iptables -A INPUT -p tcp -s --syn 192.168.0.0/255.255.255.0 -j ACCEPT &&
iptables -A OUTPUT -p tcp -s --syn 192.168.0.0/255.255.255.0 -j ACCEPT &&
iptables -A FORWARD -p tcp -s --syn 192.168.0.0/255.255.255.0 -j ACCEPT &&
iptables -A INPUT -i it -j ACCEPT
iptables -A INPUT -p tcp -s --syn 127.0.0.1/255.0.0.0 -j ACCEPT

########################################
# Sharing the web on the internal network #
########################################
iptables -t nat -A POSTROUTING -o -s 192.168.1.0/255.255.255.0 wlp2s0 -j &#8203;&#8203;MASQUERADE &&
echo 1> / proc / sys / net / ipv4 / ip_forward &&


#############
# Safety #
#############
# Protective against port scanners hidden
iptables -A INPUT -p tcp --tcp-flags SYN, ACK, FIN, RST RST -m limit --limit 1 / s -j ACCEPT

#Protecoes Attacks
iptables -A INPUT -m state --state INVALID -j DROP

# PROTECTS AGAINST Synflood.
echo "1"> / proc / sys / net / ipv4 / tcp_syncookies

# PROTECTS AGAINST BROADCASTING ICMP.
echo "1"> / proc / sys / net / ipv4 / icmp_echo_ignore_broadcasts

# BLOCKS TRACEROUTE.
iptables -A INPUT -p udp --dport 33435: 33525 -j DROP

# CLOSES ALL DOORS TABLE INPUT FOR EXTERNAL NETWORK, THE ABOVE EXETO RELEASED.
iptables -A INPUT -p tcp syn -j DROP

# Protective Against IP Spoofing
echo 1> / proc / sys / net / ipv4 / conf / all / rp_filter

# Enabling protection against bogus responses
echo 1> / proc / sys / net / ipv4 / icmp_ignore_bogus_error_responses

# Enables secure redirect packets
echo 0> / proc / sys / net / ipv4 / conf / all / accept_redirects

# Protects against ping of death
iptables -A FORWARD -p icmp --icmp-type echo-request -m limit --limit 1 / s -j ACCEPT

# Protects against attacks like "Syn-flood, DoS, etc."
iptables -A FORWARD -p tcp -m limit --limit 1 / s -j ACCEPT

# Logar packages killed by inactivity
iptables -A FORWARD -m limit --limit 3 / --limit-minute burst 3 -j LOG

# Protects against packages that can seek and obtain information from the internal network
iptables -A FORWARD --protocol --tcp tcp-flags ALL SYN, ACK -j DROP

##############
Rules # TCP #
##############
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 3128 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -p tcp --dport 3390 -j ACCEPT
iptables -A INPUT -p tcp --dport 137 -j ACCEPT
iptables -A INPUT -p tcp --dport 138 -j ACCEPT
iptables -A INPUT -p tcp --dport 139 -j ACCEPT
iptables -A INPUT -p tcp --dport 445 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 81 -j ACCEPT
iptables -A INPUT -p tcp --dport 1022 -j ACCEPT
iptables -A INPUT -p tcp --dport 143 -j ACCEPT
iptables -A INPUT -p tcp --dport 1723 -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -j ACCEPT
iptables -A INPUT -p tcp --dport 587 -j ACCEPT
iptables -A INPUT -p tcp --dport 53 -j ACCEPT
iptables -A INPUT -p tcp --dport 110 -j ACCEPT
iptables -A INPUT -p tcp --dport 3389 -j ACCEPT
iptables -A INPUT -p tcp --dport 1746 -j ACCEPT
iptables -A INPUT -p tcp --dport 20 -j ACCEPT
iptables -A INPUT -p tcp --dport 47 -j ACCEPT
iptables -A INPUT -p tcp --dport 995 -j ACCEPT
iptables -A INPUT -p tcp --dport 993 -j ACCEPT
iptables -A INPUT -p tcp --dport 465 -j ACCEPT
iptables -A INPUT -p tcp --dport 5440 -j ACCEPT
iptables -A INPUT -p tcp --dport 9000 -j ACCEPT
iptables -A INPUT -p tcp --dport 1684 -j ACCEPT
iptables -A INPUT -p tcp --dport 1624 -j ACCEPT
iptables -A INPUT -p tcp --dport 85 -j ACCEPT
iptables -A INPUT -p tcp --dport 119 -j ACCEPT
iptables -A INPUT -p tcp --dport 5060: 5070 -j ACCEPT



##############
# UDP Rules #
##############
iptables -A INPUT -p udp --dport 53 -j ACCEPT
iptables -A INPUT -p udp --dport 137 -j ACCEPT
iptables -A INPUT -p udp --dport 138 -j ACCEPT
iptables -A INPUT -p udp --dport 139 -j ACCEPT
iptables -A INPUT -p udp --dport 30606 -j ACCEPT
iptables -A INPUT -p udp --dport 3299 -j ACCEPT
iptables -A INPUT -p udp --dport 9868 -j ACCEPT
iptables -A INPUT -p udp --dport 5060: 5070 -j ACCEPT
iptables -A INPUT -p udp --dport 8766: 35000 -j ACCEPT
iptables -A INPUT -p udp --dport 995 -j ACCEPT
iptables -A INPUT -p udp --dport 993 -j ACCEPT


These rules I did not got iti manually and display the error.
I am very grateful if anyone can help.

---

### Post by ian-weisser on 2016-08-22
You will get better help by opening a new thread instead of appending to an old, unrelated thread.

---


---
title: "transparent proxy for gateway box"
date: 2005-06-27
forum: General Help
---

### Post by garbledwords on 2005-06-27
Hi,

I am having a slight bit of trouble of getting a transparent proxy set up to work right for my internet gateway box.  

My network is two PCs behind the internet gateway box.  One is on interface wlan0 and the other is on eth0.  Both of these are bridged on to interface bridge.  I have a dial-up internet connection which is ppp0.  I am trying to get transparent proxy working for the internet gateway box.  I am running Ubuntu 5.04, with Squid 2.5-STABLE8.  I set up iptables using Firestarter.  It all works fine in non-transparent mode.  

I included the following statement is squid.conf:
	httpd_accel_port 80
	httpd_accel_host virtual
	httpd_accel_with_proxy on
	httpd_accel_uses_host_header on

and the following in iptables:
	iptables -t nat -A PREROUTING -i bridge -p tcp --dport 80 -j REDIRECT --to port 3128

This now works as a transparent proxy for other computers in my network.  

But I can not figure out how to get it to be a transparent proxy for the squid box.  Could someone provide me with the exact iptables statement to do this?

Thanks in advanced.

Roy

---

### Post by apollo2011 on 2005-06-27
Please note that this post is also located at [Transparent Proxy for Gateway](http://www.ubuntuforums.org/showthread.php?t=44726) 

You should post your replies there.

If you are a moderator, you should probably delete/move this copy to prevent confusion.

---


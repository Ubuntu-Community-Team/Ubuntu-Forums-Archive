---
title: "aztech dsl 600e router"
date: 2006-11-14
forum: General Help
---

### Post by konst88 on 2006-11-14
Hello.
I installed to a friend ubuntu 6.10, and all is fine, but there is no internet.
He has aztech dsl 600e router, so it should work without any special configuration, since the router is already configured and works perfectly on XP.
I think that ubuntu recognized the router, because:
1. You can recive pings from sites.
2. You can type 10.0.0.138 and you get access to the router's configurations.
Any suggestions?
Thx.

---

### Post by CatKiller on 2006-11-14
> **konst88 said:**
> Any suggestions?

Use the Networking application to set the computer's IP address, or select DHCP, as appropriate. If you select a static IP address, put the address of the router as the gateway address.

---

### Post by konst88 on 2006-11-14
Thx for the reply.
Do you mean the address of the router as 10.0.0.138?
It is now on DHCP, and i will try the static IP option, hope it will help..
But should i leave the ip blank and only fill the gateway?

---

### Post by CatKiller on 2006-11-14
> **konst88 said:**
> Thx for the reply.
Do you mean the address of the router as 10.0.0.138?

I guess so. I've always used 192.168.1.*x* for my LANs

> It is now on DHCP, and i will try the static IP option, hope it will help..
But should i leave the ip blank and only fill the gateway?

No. If you want to specify an IP address, you have to actually specify it.

Have you "activated" eth0?

---

### Post by konst88 on 2006-11-14
Yes, now it is on DHCP and it is enabled.
So the static ip option will not work.
Should i specify a gateway for the DHCP option?
Maybe it is something in the dns tab?
Now there is only 10.0.0.138

---

### Post by CatKiller on 2006-11-14
> **konst88 said:**
> Yes, now it is on DHCP and it is enabled.
So the static ip option will not work.

That doesn't follow. It's an either/or situation. Either you are assigned an IP address by DHCP, or you specify the IP address yourself. Having it on DHCP now doesn't stop you from selecting Static IP instead.

> 
Should i specify a gateway for the DHCP option?
Maybe it is something in the dns tab?
Now there is only 10.0.0.138

As far as I know, you shouldn't need to specify a gateway address for DHCP - I think it just accepts an address from whatever device is willing to give it one. In fact, I don't think you even get the option to specify a gateway address if you select DHCP.

Is the router set up to assign addresses by DHCP? How was the computer set up in XP?

---

### Post by konst88 on 2006-11-14
In XP you only need to install the network card drivers, and there is internet connection.
In the local area connection it is written: Assignes by DHCP.

---

### Post by CatKiller on 2006-11-14
I just read your first post again. You're saying that your computer receives pings from computers on the Internet? Which would mean that you're as connected as you're going to get.

So open Firefox, type **about:config** into the address bar and then find the line that says "**network.dns.disableIPv6**" and change it to **true** and see if that helps. You might need to restart Firefox, or maybe log out and in again (I've never had to try it) for this change to take effect.

---

### Post by paddygman on 2006-11-14
as CatKiller said if you can access your router from the ubuntu machine then its not a problem with your network connection as you are connected with the network. Your problem lies either in the browser settings or in a further setting in the router that is not allowing that mac/ip/pc past it onto the internet!

---

### Post by konst88 on 2006-11-14
Thx for the replies.
I will try the solution with firefox, but i think it is not problem, because when i do : sudo aptitude update, i also gets an error something about routes.
But maybe it is connected.

---

### Post by CatKiller on 2006-11-14
> **konst88 said:**
> Thx for the replies.
I will try the solution with firefox, but i think it is not problem, because when i do : sudo aptitude update, i also gets an error something about routes.
But maybe it is connected.

Yes. Some routers have problems with IPv6. There are quite a few unresolved posts about it. Once you've established that it is an IPv6 problem by making Firefox work, you can see about disabling IPv6 for all Internet access - including aptitude. I don't know about that step, though.

---

### Post by konst88 on 2006-11-15
OK, i think you found the problem.
After i enebled network.dns.disableIPv6, FF worked perfectly, so the problem indeed is on IPV6.
But how to disable it on all the system? progrems like GAIM also doesn't work.
Thx.

---

### Post by CatKiller on 2006-11-15
> **konst88 said:**
> OK, i think you found the problem.
After i enebled network.dns.disableIPv6, FF worked perfectly, so the problem indeed is on IPV6.
But how to disable it on all the system? progrems like GAIM also doesn't work.
Thx.

I don't know. I did a search and came up with [this page]("http://doc.gwos.org/index.php/DisableIPV6"). I don't understand it, though.

---

### Post by konst88 on 2006-11-16
Ok, I managed to get it working:
In networking, a put the dns of my ISP and saved it. Now all works fine, but every reboot i neet to choose the saved location, and click apply.
Is there a way this can be automatic?
Thx.

---


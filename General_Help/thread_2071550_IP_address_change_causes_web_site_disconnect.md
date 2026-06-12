---
title: "IP address change causes web site disconnect"
date: 2012-10-15
forum: General Help
---

### Post by nuthatch3825 on 2012-10-15
I have a small web site using Apache2, PHP5 and mysql running on Ubuntu  12.04 LTS. I have the noip client running and connect to the internet  via DSL, a bridged modem and a wireless router which is shared by one  other computer. It all works hunky dory until the ISP updates the IP  address which causes a stale IP address and disconnect. Users then have  to re-enter the url and log back in. noip.com has not been able to  recommend a workaround. I'm beginning to think this is not a feasible  setup. I have searched for a similar thread in vain. Any ideas?

---

### Post by papibe on 2012-10-15
Hi nuthatch3825. Welcome to the forums! ):P

There's no solution for that problem. Hosting a website, or any other service, over a regular DHCP ISP account doesn't work very well.

For an steady service you need to invest on a static IP, a VPS, or a more permanent hosting solution.

Let us know how it goes.
Regards.

---

### Post by conradin on 2012-10-15
Did your hostname change as well?
maybe you can get by with IP address changes by reffering to the hostname.
for example:
my testing server:
```
nslookup 130.111.192.241

```
name = nanocluster.umeche.maine.edu.

my ip changes (on occasion) but my hostname has never changed. Not that it couldnt.  

You could try to make your own domain controller. Depending on what you're trying to do, it could be fun or tormenting and a source of many problems.

---

### Post by lisati on 2012-10-15
If you're lucky, your router might be able to help. Some routers come with the ability to log into services such as dyn/dyndns and no-ip and update their record of your IP address. My experience of doing it this way is that it *can* be a lot less painful than trying to install and configure a client from the DNS provider on your server.

---

### Post by nuthatch3825 on 2012-10-15
Static IP would work but it's big bucks every month. I'm not sure what a VPS is or how it works. The hostname does not change. My router does have what looks like two noip-type services I think on the DHCP disable option. If I found a router that had a noip service built in it might work but would my other computer then be hosed?

I really appreciate the help. Thanks.

---

### Post by papibe on 2012-10-15
Sorry about that :oops:. VPS stands for [Virtual Private Server]("http://en.wikipedia.org/wiki/Virtual_private_server"). For instance: [Linode]("http://www.linode.com/").

Regards.

---

### Post by nuthatch3825 on 2012-10-16
Thanks much for the info. It looks like the VPS is the best route. I wish I hadn't put the cart before the horse. 

Much obliged for the response.

---

### Post by Slim Odds on 2012-10-16
None of the suggestion here will work. If you ISP changes the IP address of your machine, it's changed. Any currently connected sessions to the old address are dead.

The dynamic IP solutions are fine for what they do: redirection a host name to an IP address (whether that address changes or not). But they can't keep a dead address alive.

The only real solution is a static IP address.

---

### Post by Wim Sturkenboom on 2012-10-16
Just host your website somewhere. Doesn't cost a fortune (unless you have a pile of databases). Converted from local currency, 750MB diskspace, unlimited BW, plus one database costs roughly US$10 / month. I don't consider that expensive and it might even be cheaper where you live.

---

### Post by nuthatch3825 on 2012-10-29
OK. I'm looking for a good host. Anyone know of any? Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-10-29
free hosting or paid hosting? i have used 000webhost worked great for a year ot so then they banned me and would not tell me why BTW there paid hosting has a max hits per minute and when you hit it your site is down for 5 min, i have used zymic worked good till they got hacked and started running there php in safe mode locking out functions i relied on, as far as paid hosting i have used i have used godaddy, there site is a PITA to use at times, but once you get everything setup and only need to use a ftp client it works fine

---


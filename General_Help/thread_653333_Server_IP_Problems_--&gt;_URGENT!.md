---
title: "Server IP Problems --&gt; URGENT!"
date: 2007-12-29
forum: General Help
---

### Post by .Shaun on 2007-12-29
Ok, everyone who goes to my external IP can access my server fine, but when they try to go to my domain name, it times out. I asked my friend to ping my site and we found out it is trying to connect to 192.168.1.101, which is my LAN IP. I am running Ubuntu Server Edition 7.10. What do I have to change?

Thanks in advance,

~Shaun

---

### Post by Craigus on 2007-12-29
What provider is hosting your internet domain?

---

### Post by .Shaun on 2007-12-29
Where did I buy the domain?

I bought it from: urlfreedom.com

---

### Post by Craigus on 2007-12-29
Are you sure everything is set up correctly at their end?

---

### Post by jim87410 on 2007-12-29
If you purchased the domain name at urlfreedom.com then they will have a DNS server that is populated with your domain name with a pointer to the IP address of the server where your website lives.

You didn't say what your domain name is.... it is interesting that the ping is returning a local (192...) address.

You also didn't say if it has ever worked or if this is a new installation.  Do you have NAT setup on your router to point a public IP address to the Private address on your server?

It is real easy to check out the DNS configuration.  I Googled "dns lookup" and went to [www.dnsstuff.com](www.dnsstuff.com) and did a DNSReport on my domain name and it showed all kinds of things.

Hope this helps some.... jim

---

### Post by .Shaun on 2007-12-29
I registered the nameservers to point to my IP. My domain is: [http://shaunsnetwork.com](http://shaunsnetwork.com) by the way, it is a new installation, and I am not sure how to setup NAT. Thanks for the reply btw.

~Shaun

---

### Post by .Shaun on 2007-12-29
BUMP - this is VERY urgent!

---

### Post by Craigus on 2007-12-30
Can you describe the network arrangement at your end - is the server connected directly to the internet / do you have a router / etc .....

---

### Post by zonky on 2007-12-30
Your name server has a loop.

see:

[www.squish.net/dnscheck](www.squish.net/dnscheck)

enter [www.shaunsnetwork.com](www.shaunsnetwork.com) and select A record:

Results

100.0% of queries will end in failure at 65.27.106.250 (ns1.shaunsnetwork.com) - nameserver loop detected

Looks a bit like you don't have a 'sticky' ip address set for ns1.shaunsnetwork.com

---

### Post by .Shaun on 2007-12-30
Ok, I see that, but how do I fix it? 

Also, I am connected via ethernet to my Linksys router.

Thanks for the help guys,

~Shaun

---

### Post by .Shaun on 2007-12-30
Bump.

---

### Post by .Shaun on 2007-12-30
Bump

---

### Post by Craigus on 2007-12-31
Some relevant discussion here:

[http://www.webhostingtalk.com/archive/index.php/t-300510.html]("http://www.webhostingtalk.com/archive/index.php/t-300510.html")

---


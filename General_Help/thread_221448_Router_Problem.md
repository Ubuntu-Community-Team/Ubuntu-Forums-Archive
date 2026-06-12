---
title: "Router Problem?"
date: 2006-07-23
forum: General Help
---

### Post by Enigmus on 2006-07-23
Hey guys. I'm new to the Ubuntu and am having problems with my router connecting to the internet.

My router is a D-Link 504-T and I am using Ubuntu 6.06 on a dual boot with Windows XP Professional

---

### Post by rowanparker on 2006-07-23
What are your problems?
Please explain more?

Rowan.

---

### Post by Enigmus on 2006-07-23
I am unable to connect to the internet. I can access places when I ping them and use their IP address such as google, but it makes it impossible for me to get packages and such

---

### Post by rowanparker on 2006-07-23
So apt fails? But pinging google doesn't?

---

### Post by Enigmus on 2006-07-23
What I mean is that whenever I try to install a package or goto a website in Firefox such as [www.google.com](www.google.com), it fails me. But if I use the Network Tools and ping [www.google.com](www.google.com) and goto the IP address it provides me, it works.

Sorry if my problem seems a little strange

---

### Post by lewmnik on 2006-07-23
Yes it is a router problem. Dapper can't find the dns-servers from your router:

1. To be able to update and just to use the net you'll have to either do it manually in /etc/resolv.conf and repeat it time after time, or disable the automated dns check altogether. (can't remember how it is done;) ) 

2. Quick fix for your Firefox is: 

```
about:config
```
in the firefox address bar and locate

```
network.dns.disableIPv6  user set boolean false
```

double click on that line = change the value to true

and you have it running again!:p

---

### Post by steverippl on 2006-07-23
You're brilliant lewnmik!! I've been having exactly the same problem with firefox for a while now, since getting a dsl modem from my isp that plays great with windows but not so great with linux. I knew it was a dns problem, but I do have the dns set in resolv.conf...?! Anyway, Firefox was still giving me problems (konqueror wasn't) until I tried your fix!

Thanks :)

---

### Post by Enigmus on 2006-07-24
Yeap! That did the trick. You rock lewmnik!

---


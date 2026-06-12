---
title: "Your connection is not secure - Firefox message"
date: 2017-08-10
forum: General Help
---

### Post by Berduchwal on 2017-08-10
Hi

```
Your connection is not secure

The owner of www.google.com has configured their web site improperly. To protect your information from being stolen, Firefox has not connected to this web site.

This site uses HTTP Strict Transport Security (HSTS) to specify that Firefox only connect to it securely. As a result, it is not possible to add an exception for this certificate.
```

Firefox 54.0 (64-bit) running on Ubuntu 16.04 LTS (Fully updated and upgraded).

This happens on occasion for all sorts of websites without any reason. 

I tried:
```
sudo /etc/init.d/dns-clean
```

PC is behind Cisco router which connects via Virgin modem. Cable connection.

I tried setting DNS to 8.8.8.8 no change.

Please suggest what else can I try.

---

### Post by TheFu on 2017-08-10
I would freak out and assume my connection was being monitored by a "state actor" - or my choice of DNS provider was flawed and my browser was being told incorrect information.  Did you validate that google's dns was actually being used?  Some ISPs capture all DNS query traffic as a "security" method.  I had to call mine to get that disabled.

From the USA (at least here), the google certs are showing green in FF. Looking at the details shows the signature tree to be "reasonable" ... signed by the internal Google CA and that is signed by Geotrust.

2 options - try some different browsers - lynx, dillo, chromium-browser, opera. What do they say?  BTW, dillo doesn't validate TLS, so it doesn't help for _THIS_ issue, but it is handy for others.  If DNS hijacking is happening, other browsers will not validate the certs any better.

Create a new userid, login with that and try FF.  If it works better, then it is a per-userid FF config/settings issue.

Regardless, get a TOR setup and/or VPN setup ASAP and see what happens when your local ISP is skipped from the connection.  ISPs around the world have decided to _monetize_ their customer's traffic.  Sometimes they do small trials with a few subnets and don't tell anyone.

Also, I'd check the Cisco for hacks and also look for a newer firmware to be installed.  If it is over a month old, I'd  look for a replacement that has constant, weekly (or more often) patching methods.  I don't believe any consumer router is properly maintained these days and many enterprise edge routers are not either.

My ISP requires that I use their Cisco router, but I configured it to be in "bridge mode" and run my own router (with pfsense) behind it. MY router handles the public IPs.  I use the Cisco router for guest access and for the kid's games.  My stuff is inside, secured, with fairly quick router software updates.

Hopefully, someone with less paranoia will reply too.

---

### Post by Berduchwal on 2017-08-11
Hi

Thanks for your response. I now learned that this issue is common with Cisco routers:
[https://supportforums.cisco.com/discussion/12485071/ssl-certificate-errors-websites-using-cisco-rv130-router]("https://supportforums.cisco.com/discussion/12485071/ssl-certificate-errors-websites-using-cisco-rv130-router")

---

### Post by TheFu on 2017-08-11
Please mark the thread **solved** to help the community out.

---


---
title: "Ugh, someone hacked into my FTP!"
date: 2008-03-09
forum: General Help
---

### Post by Airjoe on 2008-03-09
When I woke up this morning, I noticed the activity LED on my Wifi card was going crazy, something unusual since I only host a couple tiny websites. I logged in to my router and saw tons of requests to my linux box on port 21. I immediately SSH'd in and blocked the IP with iptables, but I'm sure they're coming back. 

Is there any way to tell what user they logged in as, or what files they downloaded? When it comes down to it, there's nothing really important on the box, it's just scary as heck. 

Also, is there a way to prevent this? I imagine they bruteforced. How can I make it disable connections after X failed attempts?


Thanks!

---

### Post by .nedberg on 2008-03-09
Read the logs! If you use vsftp /var/log/vsftpd.log (I think, you'll find it)

fail2ban can auto-block an IP after X attempts!

---

### Post by HermanAB on 2008-03-09
Look at the logs to see whether they really got in.  Brute force attacks are very common and this is why you have to use proper passwords for all accounts (>8 characters).

You can prevent any and all brute force attacks very easily with an iptables rate limiting filter in /etc/rc.d/rc.local:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

A rate limiter will make any brute force attack impractical and should be part of every firewall.

Cheers,

Herman

---


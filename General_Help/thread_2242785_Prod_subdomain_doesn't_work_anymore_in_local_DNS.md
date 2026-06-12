---
title: "Prod subdomain doesn't work anymore in local DNS"
date: 2014-09-04
forum: General Help
---

### Post by Colin_Deisenroth on 2014-09-04
I am using bind9 for my dns server, and have some subdomains in there as well for "dev", "qa", "staging," "prod" etc

So, in my resolv.conf I have search example.com and I can type "ssh [email]user@server1.dev[/email]" or ssh [email]user@server1.prod[/email]" and it will find server1.dev.example.com in my local dns. All the domains still work, except ".prod" doesn't work anymore unless I type the full "server1.prod.example.com" fqdn. I think this may be because there is a ".prod" domain on the internet now, and my dns is trying to send me to that instead of appending my local domain to the end like it used to.

1) Anyone know how to verify if this is the case? Pinging anything.prod gives me 127.0.53.53 right now. Are others seeing the same result?
2) Anyone know how to make my local bind server respond to "ping server1.prod" by pinging server1.prod.example.com from my local dns A record?

Thanks!

---

### Post by Colin_Deisenroth on 2014-09-04
I figured it out myself.

Anytime you have a . (dot) in your ping or ssh command, it considers it a fully qualified domain name. So when I do "ssh server1.prod" it thinks that's a real domain name. Usually when you do this, it doesn't find it, so it tries with your dns search domain at the end and then it works. If the domain exists though, usually you're out of luck. Like if you wanted to make a subdomain called "com". So your example domain would be "server1.com.example.com" but that would actually look for server1.com instead.

To fix this, I had to edit my resolv.conf file to tell it that only if the name has TWO dots, it should be considered a real domain, otherwise check my local dns domain.

So my /etc/resolv.conf file looks like this now

options ndots:2
search example.com
nameserver 10.1.1.1

If you're using a newer version of ubuntu, this file will get overwritten by the resolvconf program, so I had to add "options ndots:2" to
sudo vi /etc/resolvconf/resolv.conf.d/head

---


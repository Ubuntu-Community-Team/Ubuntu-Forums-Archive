---
title: "Web Server: Using A GoDaddy subdomain with my AWS server"
date: 2017-08-09
forum: General Help
---

### Post by vanzee on 2017-08-09
I'm fairly new to the admin side of Linux, especially when it comes to Ubuntu Web Server. I've been building websites since the 90s, but generally don't go much deeper than my web hosting company's cPanel interface + Filezilla for folder permissions and uploading.

At my job I've been developing some web apps and we'd like to use subdomains from the domain name we purchased with GoDaddy. Unfortunately the options seem to be limited. They have forwarding which will show up as the IP address in the browser, or Forwarding with Masking where the domain name shows up but it displays the actual website in an iFrame which keeps the URL bar from updating and keeps breaking certain aspects of the site.

What are my options with my Ubuntu Web Server? Is there any way to connect it with my DNS settings on GoDaddy so going to sub.domain.com actually takes people to sub.domain.com.

Thanks in advance for any assistance. I know getting hit with dumb questions all the time probably sucks. I have looked into it, but I figured I'd ask some experts for the best practice so I don't screw it up.

---

### Post by dragonfly41 on 2017-08-10
I have never used GoDaddy.  

But I have used web hosting services with similar forwarding restrictions.  In my case after the registrar gave me good notice of their closing down registrar services I smoothly migrated all my several domains to google domains [https://domains.google/](https://domains.google/)  and I set up account with google cloud (which credits $300 for startup usage).

You have your server on AWS.

Here are some links which might help your case.


[https://www.bersling.com/2017/01/27/migrating-from-godaddy-to-aws-route-53/](https://www.bersling.com/2017/01/27/migrating-from-godaddy-to-aws-route-53/)

[https://stackoverflow.com/questions/40213163/migrating-of-dns-from-godaddy-to-aws](https://stackoverflow.com/questions/40213163/migrating-of-dns-from-godaddy-to-aws)

[http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html)


And this is useful for monitoring DNS ...

[http://www.squish.net/dnscheck/simple/](http://www.squish.net/dnscheck/simple/)

You might also explore ...

[https://www.zoneedit.com/](https://www.zoneedit.com/)

---

### Post by vanzee on 2017-08-10
Thanks so much for the info!

---


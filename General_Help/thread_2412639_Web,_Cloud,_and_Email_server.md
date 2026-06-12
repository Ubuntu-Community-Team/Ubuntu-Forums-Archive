---
title: "Web, Cloud, and Email server"
date: 2019-02-15
forum: General Help
---

### Post by PantherStu on 2019-02-15
Hi All.


I Need some help, I am working with an Animal rescue, and have been in charge of the web page hosting. I have been asked if we can save any money on our web etc hosting, so was thinking as I have an unlimited internet and a spare PC with Ubuntu 18.10 on it, that I could possibly host our current wordpress site, emails and a cloud server direct from this.

What I am trying to find out, 
1. What do I need to setup and any suggestions for web server.
2. What email server and how to set up.
3. A cloud server, I have been looking at next cloud, but am open to other suggestions. and how I would set up.


Any ideas, suggestions are greatly appreciated.

Thanks in advance

---

### Post by TheFu on 2019-02-15
$5/month is too much?

You should never mix personal with business.  There are many, many, reasons for this.  Plus, it is likely that your ISP has prohibitions against running public servers in the contract and also has down time that you don't know about.  For example, at my home this week, my logs should 30 minutes of downtime.  I didn't notice, but a business would definitely notice.  Last week was down 84 minutes.  The week before was down 58min.


Almost nobody should run their own email server these days. I do it only because I've been running email servers for work since the mid-90s.  Running email from a home IP is next to impossible without having a server in a data center somewhere to be the in/out gateway.  I block all email from residential internet connections. Almost all the professionals do this since it is always spam.  I have an email gateway (Scrollout) and run a Zimbra communications server for a few businesses, family, and friends.  Zimbra is a hog and can't be installed on an old system that is lying around.  But zimbra has a beautiful webapp for end-users, honors all the normal standards, CalDAV for calendaring.  Centralized address books, shared anything using group permissions, etc.  I'm completely addicted to Zimbra's enterprise calendaring capabilities.  It is nice to have delegation capabilities so someone trusted can manage my calendar, but not have other access.  Did I mention that Zimbra was a hog?  It wants lots of RAM and lots of CPU - when compared to any other alternative, except MS-Exchange.  Zimbra is lite compared to Exchange.

Probably what you want is "**The Perfect Server**" setup. Just google that.  Also, for production, never, ever, use non-LTS server releases.    You should use 18.04.x or 16.04.x at this point.  Definitely NOT 18.10.

Running wordpress on your HOME LAN is asking to be hacked unless you are a php security guru.  Keep WP on someone else's network, so when it gets hacked, you haven't just leaked everything on your HOME LAN to the world too.

A few other considerations ... how long will your computers run when the power is out?  Does the ISP keep working?  We have great power here - only storms take it offline, yet there are a few 2-20 min outages every year.  Every 2-3 yrs, there is a 4-8 hour outage for some other reason.

I use nextcloud, but only allow access through a full VPN from place on the internet.  I simply don't trust my php skills to properly secure web-apps based on php sufficiently to trust them.  An SSL HTTPS cert isn't security, it is privacy between the client and the server.  Nextcloud is ok, but not the greatest thing, IMHO.  I'm old and have been doing things that nextcloud provides over ssh, rsync, and with other techniques for a few decades.  Basically, I use nextcloud as an easy way to get music onto my phone, but really nothing else.

Backups.  Can you do daily backup without any downtime for all these servers.  Where will the off-site backups go?  What sort of backup infrastructure do you have at home?

Ok ... so those are the big reasons NOT to host this at home.  But, you definitely should setup a home server and try to setup all these things without allowing internet access.  Then you can setup the same stuff at a VPS you control much faster and use best practices to have backups both at the VPS and in your home.  If the VPS gives you issues, moving to another $5/month provider is much easier.  If the issues are really bad, you can host some of the needs using your cloned setup at home for a few days.  Just modify the DNS.

If you have questions about _why_ I said some of those things and didn't make clear, feel free to ask.

---

### Post by SeijiSensei on 2019-02-15
I can't say enough good things about Linode.  [https://www.linode.com/pricing](https://www.linode.com/pricing)

You don't want to run your own mail server.  I manage mail for some clients and have years of experience.  It's still a pain in the butt.  If your organization has a domain, and you want to have [email]user@domain.name[/email] mailboxes, look into hosted services like those Google offers. 

Start small.  Install Apache on a Ubuntu machine you have now. Migrate the current web content to it. Make sure you can see everything over the local network. Once you can do that on your own machine, migrate the site to a server in the cloud.

WordPress does demand your attention since it is updated rather frequently.  Everyone and his brother is looking for vulnerabilities in WP, so it's always a race to keep up.

---


---
title: "Webmail Help"
date: 2021-04-24
forum: General Help
---

### Post by overcon on 2021-04-24
Hi All,

I need some help with setting up a mail server and access to the webpage for its webmail and management. Some specifications on what I have running now. I am running pfSense as the firewall. Behind that, I have a Raspberry Pi 4 that is running Apache 2.4.41. That apache server on the RBPI4 has a couple of domains hosted on it, one of them is a page for my weather station. On the firewall, I have ports 80 and 443 NAT'd to the RBPI to access those web pages.

I then set up a virtual server running Ubuntu 20.04 and used the guide [here]("https://www.linuxbabe.com/mail-server/ubuntu-20-04-iredmail-server-installation") to install a mail server. It's running, but I need a way to redirect traffic to the webserver running on it instead of the RBPI for the webmail, short of running it all on the RBPI. I don't have a lot of experience with Apache, so I hope someone can help me come up with a solution so I can use the webmail and the management interface for the mail server and maintain my webpages on the RBPI.

I appreciate any help in getting this working.

---

### Post by TheFu on 2021-04-24
Do you have a static IP and DNS record MX setup?  Without those nobody else will email you or accept email from your system.

On the systems that are not the mail email server, just setup a postfix satellite MTA.  This will only accept email from localhost (the machine) and not over the network.  In the installer, it will ask where to forward all mail - use the IP address of the mail email server. This will forward mail based on the /etc/aliases setup to the other box using normal SMTP.

On the main email server, it needs to accept SMTP from the systems you setup as satellite.
No way would I allow web access to webmail over the internet.  Only allow LAN access and force a VPN be used. This applies for IMAPS as well.  It is too easy for someone really new to email to have their setup hacked, so just best to avoid that.  I've been running email servers since the mid-1990s and force using a VPN on all the users. No exceptions.  If the rpi is on a different LAN from the mail mail server, you can specify which hosts by IP are allowed to send as part of the same domain.

Be certain that any machines which are allowed to send email are in the DNS TXT SPF record.  Those are fairly simple for a single subnet, but can become complex if you allow other senders (like marketing/advertising) to send email on the domain's behalf.  All the DNS records are public, so there are literally millions of examples for your viewing pleasure.

I've never used iredmail. Can't help with that. Sorry.

---

### Post by overcon on 2021-04-24
Hi, yes, I have DNS and reverse DNS records set up, along with a static IP. This is the first email server I have tried setting up. I have an SSL certificate I can get for it as well for the webmail portion. 

This is all running on the same subnet, I haven't set up VLANs yet, though I do plan on trying to get that all set up. I have an older Cisco 48 port c3750P switch, which is a nice older switch, but works. This is a separate network from my actual network, so everything on it is designed around the weather station. I use the network to learn how to do stuff and for tinkering and trying stuff out.

So I want to look into the Postfix MTA? 

Thanks!

---

### Post by TheFu on 2021-04-24
Postfix is a security-centric MTA that has been around since the mid-1990s. Most email servers probably use postfix, unless they are an ISP ... or, cough, from that other OS company which had a huge exploit the last month or so.

Postfix can be setup in many different ways.  
[LIST]
[*]I have about 15 **satellite postfix** setups for all my systems. That includes desktops/laptops.  If it runs Unix/Linux/BSD, then it has postfix setup.
[*]I have 2 **SMTP gateways**, which filters all inbound and outbound email traffic. It is server-to-server only. It is the only way SMTP gets in or out of the network. Period.
[*]I have 1 main "**communications server**" that is what users connect with using either SMTPS or IMAPS or the built-in webmail capabilities. That can only be reached from one of the internal LANs or using a VPN to exit onto the server LAN. In theory, this full server could be placed onto the internet, but I'd expect it to be hacked within a week. It has so many capabilities and tightly coupled subsystems that I simply don't trust it.
[/LIST]
When the mail email server isn't available, the gateways accept mail and hold it until it can be forwarded.

The underlying OS for all these get patched weekly. This isn't the 1990s anymore. The internet isn't safe. If something can't be patched weekly, then I'm not really going to trust it.  There may not be patches every week, but there usually are, even for the WAN router.

---

### Post by SeijiSensei on 2021-04-25
Is it worth $5-10/month to get all this infrastructure out of your physical location and into the cloud?  I'd lease a [Linode]("https://www.linode.com/pricing") and build the webmail server there. 

My only experience with webmail software was a very early version of Horde.  The current implementation looks very nice: [https://www.horde.org/apps/webmail/screenshots](https://www.horde.org/apps/webmail/screenshots)

---

### Post by TheFu on 2021-04-25
> **SeijiSensei said:**
> Is it worth $5-10/month to get all this infrastructure out of your physical location and into the cloud?  I'd lease a [Linode]("https://www.linode.com/pricing") and build the webmail server there. 

My only experience with webmail software was a very early version of Horde.  The current implementation looks very nice: [https://www.horde.org/apps/webmail/screenshots](https://www.horde.org/apps/webmail/screenshots)

Definitely put the gateway into the cloud, but there are reasons to keep the real mail server and storage local, under your physical control.

---


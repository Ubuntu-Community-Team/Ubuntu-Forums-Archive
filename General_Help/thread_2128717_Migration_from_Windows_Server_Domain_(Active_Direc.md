---
title: "Migration from Windows Server Domain (Active Directory) to Ubuntu Server Directory"
date: 2013-03-24
forum: General Help
---

### Post by Alan5127 on 2013-03-24
Hi All,

[COLOR=#ff0000]**Short Version - What directory service should I use?**[/COLOR]

I have a domain that I am administering for a small business, currently running a Windows SBS 2003 server, and five users (each with a separate machine two of which are laptops) including me, all of us using WinXP Pro on the domain.

The desktops / laptops are fine (for now), but the server is in need of replacement.

The SBS Server provides:

Exchange Mail Server
File Serving
Proxy (it is dual-homed) - Uses ISA (router will only allow traffic out from the Server, so all desktops must proxy through the server)
DNS
DHCP
Print Serving (two printers, one an HP Laserjet, the other a Konica Minolta multi-function printer, scanner, copier, outgoing fax machine)
Incoming faxes
Active Directory
Remote Access to user machines (RWW) assuming they are left on


Rather than spend the huge amounts that MS want for their latest Server 2012 which we cannot afford, I figured I would look at replacing the server with one (or more if required) machines running Ubuntu (which I use at home on a desktop and dual booted on my work laptop) to replace whatever I can from the above list.


Rather than a single 'big bang' I also figured it would be easier for me if I transferred services from the SBS box to the new Ubuntu Server one at a time.

I thought the following:


1) Exchange Mail Server:

   Move to Google Apps (this would also make remote access to email easy for users and make them generally happy)


2) File Serving:

   Put on the New Ubuntu Server


3) Proxy:

   Set up a separate box running Privoxy or something similar, and force all connections through there - seems easy


4) DNS:

   Configure this on the router.


5) DHCP:

   Configure this on the router.


6) Print Serving:

   Put this on the New Ubuntu Server


7) Incoming faxes:

Have the Konica answer incoming faxes, and go back to actual pieces of paper for now (volume very low anyway)


8)  Directory Services / Users:

   This is the one that I need help on most, and hence this post.


9) Remote Access:

   Hoping that this can be allowed somehow using the Ubuntu Server, but other options may have to be considered.


I have searched on this site, and there are many mentions of OpenLDAP, so right now, that seems to be the way to go.  However, I would like to get recommendations from you all, and specifically, why you think that something would be better / easier / more supported (including on here) than going with OpenLDAP.

For the avoidance of doubt, I would likely come back to the list above later, and revisit putting more of the services on the Ubuntu Box (I would like to have an in-house mail server, and Google is now charging, albeit only $5 / user / month or $50 a year I think), but I have to be able to setup and maintain users (a la Active Directory) first.

Also, just in case anything gets the wrong idea, it does not matter if the solution is AD compatible - the SBS box will be going away entirely, and we will be migrating off MS Windows Server, so as long as WinXP Pro SP3 (and later Windows versions) can connect to the server, and be authenticated by it, that is fine.  We may replace the desktops with Ubuntu later, but for now, they will be staying in place, including the laptops (mine is dual booting Win7 with MS Office 2010 (not joined to the domain) and Ubuntu, with WinXP Pro with Office 2007 running in a VM under Ubuntu VirtualBox).


So, OpenLDAP?  If not, why something else?

If OpenLDAP, what is the best guide for setting it up on Ubuntu Server around right now?


Thanks in advance,

Alan.

---

### Post by SeijiSensei on 2013-03-25
> **Alan5127 said:**
> 
1) Exchange Mail Server:

Move to Google Apps (this would also make remote access to email easy for users and make them generally happy)

Exchange provides other services like calendaring, room and resource reservations, and the like.  Have you polled your users to see what they use Exchange for?  I would never make a change of this magnitude without interviewing the users about what they use and how they use it.

2) File Serving:
6) Print Serving:

Samba is fine.  You might want to look into [Samba 4]("https://fosdem.org/2013/interviews/2013-jeremy-allison/") which is designed to emulate more of the features found in Active Directory.

3) Proxy:

I usually install Squid on a router with two Ethernet connectors, one pointing to the Internet and the other designated as the internal network's default gateway.  It runs in "transparent" mode with the appropriate iptables rule to push all requests for remote port 80 through the proxy.  Proxying HTTPS connections is a whole 'nother ball game, though, since the proxy will appear to the client browser as the source of a "man-in-the-middle" attack.  We control HTTPS by iptables rules that block sites like Facebook and YouTube.  The Squid developers have been working on [another solution]("http://wiki.squid-cache.org/Features/SslBump") that intercepts the connection and substitutes the proxy's certificate for that of the remote site.  This requires deploying certs to all the internal browsers and doesn't yet work in transparent mode.

We also use [SquidClamAV]("http://squidclamav.darold.net/") to scan every downloaded object for viruses.  This box has a couple hundred clients behind it, and it does a variety of other things like Web and DNS services and email virus and spam scanning with [MailScanner](http://www.mailscanner.info/).  As a result it's a pretty hefty box, a Dell Poweredge 410 with dual Xeons and 8 GB of memory.  It still has a load average under 1.0 nearly all the time.

4) DNS:
5) DHCP:

Or configure the Linux box to provide these services.  ISC's bind9 and dhcpd servers can populate the zone files for machines that receive an address via DHCP.

7) Incoming faxes:

[Hylafax]("http://www.hylafax.org/content/Main_Page") is a tried-and-true fax server for *nix machines.

8)  Directory Services / Users:

Take a look at Samba 4.

> 9) Remote Access:
Hoping that this can be allowed somehow using the Ubuntu Server, but other options may have to be considered.

Text-mode access to the server is usually handled by SSH.  If you want users to have remote access to their desktops, I think you can set that up without needing the Ubuntu box at all.  Another option to consider is [GoToMyPc]("http://www.gotomypc.com/remote_access/remote_access"), which is a more secure solution than letting people connect directly to the network from outside.

I've always found OpenLDAP, and LDAP in general, a royal pain in the butt.  That's one reason I suggested Samba 4 as an alternative as it might be easier to configure.

---

### Post by dcstar on 2013-03-27
If you really want to go the painless route, you get on eBay and purchase a cheap copy of SBS 2008 or SBS 2011 and just upgrade (convert the existing one and put it in a free VMware ESXi hypervisor).

I deal with SBS for a living and have been using Linux at home for a long time, and I still would not use Linux to replace it as the administration change from the existing setup will be a nightmare.

Don't forget that support for XP stops in April 2014.

---


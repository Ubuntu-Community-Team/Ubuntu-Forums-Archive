---
title: "DYNDNS issues"
date: 2007-06-10
forum: General Help
---

### Post by spotslayer on 2007-06-10
Hi guys, I have been using dyndns for over two years to access my home network from wherever. This morning I cannot access my network using the the url. If I put in the public IP I can still access my network. I have been googling all day today but have not found an answer or even a similar problem. When I enter xxxx.is-a-geek.com it times out. I get the public IP from IP chicken and it will work sorta. Since my wordpress and other web apps are not set to use the public IP(which changes due to my isp) they don't load the proper pages. Any ideas?

David

---

### Post by arvevans on 2007-06-13
The DYNDNS site provides configuration information to use with "ddclient" for correcting your public IP address on DYNDNS when you reboot and at regular intervals after that.  Go into Synaptic Package Manager and download & install "ddclient".  Then after it is installed use the DYNDNS information to configure it to use their IP-checking method so that your actual public IP address will be registered instead of your local LAN IP address.  This works for me.
_._

---


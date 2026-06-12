---
title: "Can I compile 3rd party apps?"
date: 2005-04-08
forum: General Help
---

### Post by Malkosha on 2005-04-08
I'm a Linux noob. I have ran SimplyMepis 3.3 and I'm now running Fedora Core. Most of the time I'm not really sure of what I'm doing when I set things up and install them, but I'm pretty good at following directions.

I love the Debian apt-get system. While FC has its "yum" system for RPM's its not nearly as robust. It would be great to be able to go back to a Debian based distro. What drove me away from Mepis was that I need to be able to run these three apps:

P2P/Cedega
Cisco VPN
Citrix

While I can always manage to get Cedga running in Mepis or any other distro, I could never get the Cisco client to install. This was due to not being able to get the sources I needed to compile a kernel module (I think this is the correct term ... hey I'm new here cut me some slack :D) This wasn't a problem in Fedora Core and everything worked there great.

I would love to try Ubuntu. but only if it will let me install my third party programs. Is this a problem in Ubuntu? Is there anything I would have to do in a general sense like install the sources or headers .... or whatever? If I'm being vauge I'm sorry but I figure if I keep on trying sooner or later I'll understand it all but until then I may have a translation problem ... if you know what I mean.

Thanks in adavance for the help!!

---

### Post by az on 2005-04-08
Out-of-the-box, using just the install cd, yes:

sudo apt-get install build-essential linux-headers-2.6.10.5

---


---
title: "[SOLVED] Citrix woes in Hardy"
date: 2008-04-27
forum: General Help
---

### Post by MoebusNet on 2008-04-27
SOLVED

Clean install of Ubuntu 8.04. Followed this guide: [http://roner70.blogspot.com/2007/08/citrix-ica-client-to-work-in-ubuntu.html](http://roner70.blogspot.com/2007/08/citrix-ica-client-to-work-in-ubuntu.html)

Command-line install failed (I didn't notice that it is now called ICAClient-10.6-2.i386.deb after converting to .deb) so I double-clicked on the .deb package and let it install from the Desktop.

I can sign in to the log-in page, but when I click on the Main Desktop, I get a message that asks me what to do with launch.ica file (open with... or save).

EDIT: The referenced guide didn't work for me. I found another guide link from the forum at [http://wass.homelinux.net/howtos/Citrix_ICA_How-To](http://wass.homelinux.net/howtos/Citrix_ICA_How-To) 

This guide worked for me with some changes. The link for the "current Linux x86 tarball" is actually the _German_ language tarball (notice the .../de/... in the file name). After accidentally installing the German variety, I had to go to Synaptic to uninstall it. Downloading the English version from [http://www.citrix.com](http://www.citrix.com), notice it is named "en.linuxx.tar.gz" . That will be what you use to unpack the tarball. The author recommends answering "No" to the installer's offer to integrate Citrix automatically with the browser. I couldn't accomplish the setup for the plugins, but Citrix works well enough for my needs. YMMV!

Moderators - Please mark this as 'SOLVED'

---

### Post by El Puño on 2008-06-01
I can't understand why Citrix is not able (or willing) to make a real Ctrix client (like the Windows one) to Linux ???

Installing the ICA client is horrible, not to mention getting it running  :(

---

### Post by MarlowH on 2008-06-07
Advice from MoebusNet worked great for me on Hardy amd64, but I found two differences from the instructions.

Instructions predict firefox plugins at /opt/firefox/plugins/  but I found it at /usr/lib/firefox/plugins

Instructions predict wfica at /usr/lib/ICAClient/wfica  but I found it at /home/<my_id>/ICAClient/linuxx86

---

### Post by ssavelan on 2008-08-04
Been working with quite a few blogs/discussions/resources... still no luck with 10.6 /Hardy..

your roner70 link is broken too

---

### Post by ssavelan on 2008-08-04
I have tried everything that I can find.  I almost think that the variability in solutions might be due to proprietary video issues.  Still trying but the links presented above certainly do not constitute "SOLVED" for me...

trying to put 10.6 in Hardy ...

---


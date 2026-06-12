---
title: "win32 file sharing and remote desktop"
date: 2005-08-07
forum: General Help
---

### Post by blu.gecko on 2005-08-07
is it possible to view nd share files with other win32 systems on my home network? when I say share, I mean if they have a share folder can I view it, add to is and so on, also can I remote destop to another pc, like I have done through my windows partition.

thanks in advance for all the info.

blu

---

### Post by dieselpower on 2005-08-08
Yes you can share files. Go to Main Menu > System > Administration and click on networking. If you have a ethernet card in the computer there should be an entry marked "ETHERNET CONNECTION, the interface eth0 is inactive". 
Click on it and then click the properties button. 
Tick the checkbox that says "This device is configured".
If you have a DHCP server, AKA "automatic network setup" choose DHCP. You're done! Otherwise read on.
Choose an IP address, such as 192.168.0.3, and enter it.
Click in the subnet mask field. It will automaticaly fill in with the right address.
If you have a machine with internet connection sharing enabled, type it's IP address in the "Gatway Address" field
click OK
Click on the General tab and make sure your host name is what you want.
If you have internet connection sharing. Click on the DNS tab, call yore isp and ask for thier domain name servers, and enter at least one. and click OK.

Now go to Main Menu > Places and click on Network Servers and hopfully everything will show up there!

---

### Post by wellery on 2005-08-08
As for remote desktop there is this:

[http://sourceforge.net/projects/rdesktop/](http://sourceforge.net/projects/rdesktop/)

which I'm not sure but I had it installed. It may already be installed by default. If it's not installed it's in the base repositories.

---


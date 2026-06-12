---
title: "IPBlock issues"
date: 2008-01-08
forum: General Help
---

### Post by FreakTech on 2008-01-08
I installed IPBlock on my system and when I enabled it I lost my internet connection.  Once it is disabled I am able to connect again. 

I have gone in and set it to ignore HTTP and HTTPS ports, but this still has not fixed the problem.  I am at a loss.

Any help would be greatly appreciated.

---

### Post by uljanow on 2008-01-08
Are there any log entries of blocked IP addresses ? Maybe your ISP is being blocked and needs to be whitelisted.

---

### Post by FreakTech on 2008-01-08
I'm not sure.  Under the List tab there isn't anything list except the ones that come as default.  Where would I look for this?

---

### Post by uljanow on 2008-01-08
The first tab shows the blocked IPs, which are also logged to **/tmp/ipblock.log**. But the log does not survive a reboot, so it might be required to enable it again.

---

### Post by herrdoktor330 on 2008-02-22
I'm also having a major problem with IPBlock under xubuntu 7.10. I followed the instructions to install IPBlock, and one of the dependencies (libnfnetlink0) broke my apt-get.

Any suggestions there?

Edit: I'm an r-tard... wasn't using the right version of the package.

---


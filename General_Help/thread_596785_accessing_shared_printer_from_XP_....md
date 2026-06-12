---
title: "accessing shared printer from XP ..."
date: 2007-10-29
forum: General Help
---

### Post by thatcher695 on 2007-10-29
I'm running 7.10.  I installed a local printer; designated it shared and accessible by anyone.  In windows XP i installed the shared printer but the printer shows access denied when I attempt to print.  What am I missing?  Do I need to configure samba?  If so why is windows XP able to see the printer and install from the ubuntu system?

---

### Post by fsman on 2007-11-09
i followed the network printing guide.
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
also the release notes [http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710) 
regarding the apparmor so I also ran 
sudo aa-complain cupsd


Still get access denied on my windows2000 box.

Only workaround I found was to restart "printer Service (cupsys)"
system-apps-services

then windows can access the printer.

Also - I found that using hostname doesn't work I have to use the local ip address.


Anyone have an idea why people are getting "access denied" when following the gutsy guide?

---


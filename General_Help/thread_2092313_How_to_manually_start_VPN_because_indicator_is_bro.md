---
title: "How to manually start VPN because indicator is broken?"
date: 2012-12-07
forum: General Help
---

### Post by hangfire on 2012-12-07
Hi,

After setting up multiple advanced users with VPN, they are often unable to use it because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1006141](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1006141)

also

[https://bugs.launchpad.net/ubuntu/+source/indicator-network/+bug/868587](https://bugs.launchpad.net/ubuntu/+source/indicator-network/+bug/868587)

There's been no progress on this bug in months.

Is there a command-line way to start VPN? 

Thanks 
HF

---

### Post by hangfire on 2012-12-07
Never mind I just found the answer on askubuntu:

[http://askubuntu.com/questions/57339/connect-disconnect-from-vpn-from-the-command-line](http://askubuntu.com/questions/57339/connect-disconnect-from-vpn-from-the-command-line)

nmcli con up id "VPN Friendly Name"

---


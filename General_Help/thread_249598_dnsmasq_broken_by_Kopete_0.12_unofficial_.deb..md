---
title: "dnsmasq broken by Kopete 0.12 unofficial .deb."
date: 2006-09-02
forum: General Help
---

### Post by AirRaven on 2006-09-02
I've been using the "dnsmasq" utility to run a local DNS cache on my Ubuntu box for a while now, and it's worked absolutely perfectly at removing all the problems I've had with IPv6 addresses slowing down my DNS access.

Unfortunately, I've just installed an unofficial .deb package of the Kopete instant messenger from [this thread](http://www.ubuntuforums.org/showthread.php?t=190273), more specifically, the version linked to [here](http://www.ubuntuforums.org/showpost.php?p=1140248&postcount=4). It worked fine for the rest of the session I was using, but the next time I rebooted, no internet sites seemed to work. After a bit of poking around, I discovered it had broken dnsmasq, and I fixed the problem by using my ISP's DNS servers as my DNS servers. This solved the problem, and I uninstalled dnsmasq via Synaptic. Unfortunately, the changes I had made don't "stick" after each reboot now- I have to manually specify my DNS servers every time I boot up in Network Settings.

I've tried the Kopete packages linked to at the end of the thread I linked to, but they don't remedy the problem. 

Does anybody know how I can get dnsmasq up and running again? If not, is there any way of stopping my DNS servers from being resetted after every reboot?

EDIT: I set up dnsmasq by using the instructions shown in this site:
[Here](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

---


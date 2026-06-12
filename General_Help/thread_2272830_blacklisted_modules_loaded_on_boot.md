---
title: "blacklisted modules loaded on boot"
date: 2015-04-08
forum: General Help
---

### Post by Miles_Prower on 2015-04-08
So I have a dell inspiron 1501 from way back that I reinstalled ubuntu on.

The wireless card for this laptop has never worked fresh from installation, and this time I'm using this guide to set it up: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I've blacklisted some kernel modules that conflict with ndiwsrapper, but they still appear to be loading on boot. 
[http://pastebin.com/siKpFk7Y](http://pastebin.com/siKpFk7Y)

Also I try to tail or cat /var/log/messages but it's not there. 
Anyway what would make these kernel modules still load despite being blacklisted? Is that not the right name for the blacklist? 

Thanks

---

### Post by steeldriver on 2015-04-08
IIRC files in /etc/modprobe.d are only processed if they have a .conf extension. Your system probably already has a default /etc/modprobe.d/blacklist.conf file though - so your options are either to add the additional modules you want to blacklist to that, or (preferably IMHO - makes it more traceable) rename your 'blacklist' file to something like'blacklist-b43.conf'

---

### Post by Miles_Prower on 2015-04-09
That was 100% correct. I tab completed to /etc/blacklist and assumed it was an existing file. Wireless still doesn't work but I'll experiment with kernel modules and see what I can come up with.

---


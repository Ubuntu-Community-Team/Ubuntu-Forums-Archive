---
title: "Ubuntu In Vmware (Windows 2003 server) Bridged Network"
date: 2006-11-21
forum: General Help
---

### Post by anon1234 on 2006-11-21
I'm running Ubuntu in Vmware Server edition on Windows 2003. 

I have it set on a bridged network,

I went into System - Administration - Networking

I set a static ip address, added dns and gateway settings and set eth1 as default gateway device.

The net still isnt working though, i tried pinging google and my windows ip with no luck, i can ping my linux ip from windows though..

---

### Post by janstedehouder on 2006-11-23
Just to clarify things: what are you trying to do with it?

One thing that pops to my mind is to check the settings in Windows 2003. By default the Windows 2003 security settings are quite high and it could be that what you are trying to do is not allowed yet.

---

### Post by anon1234 on 2006-11-23
> Just to clarify things: what are you trying to do with it?

What do you mean?

---

### Post by jav on 2008-02-08
Check if you have any contents in "/etc/resolv.conf"
If you don't then you can't ping e.g. google because it cannot resolve the address.

If it's empty, then do ipconfig /all on your winbox, and check the DNS server and put it in resolv.conf as

```
nameserver <DNS-ip>
```

---


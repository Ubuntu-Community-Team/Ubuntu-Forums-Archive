---
title: "ddclient: Is this DDNS client updating conditionally based upon IP change?"
date: 2013-04-25
forum: General Help
---

### Post by held7over on 2013-04-25
Ubuntu 12.04 ddclient

I am not using ipcheck with any service. Instead, I am running ddclient as a daemon on my system which directly read's my modem's external IP and then updates my domain host's records to reflect my external IP.

I have noticed that the daemon setting inside /etc/ddclient.conf 

```
# update time in seconds
daemon=300
```

-is in seconds and that many google searches show people setting this for 5 minutes to a couple of hours. 

This makes me wonder if ddclient is actually doing an update to my domain host each timeout or if it is first checking to see if my external IP has actually changed before it decides whether or not to take action and hassle my domain host service with an update?  (I had ASSUMED it was this last method...but now, am not so sure...)

Does anyone know if their is a conditional check before it acts to update my domain host service???  i.e. Are they going to ban me at any moment from using DDNS!!!

Thanks! I appreciate your thoughts on this.  :)

---

### Post by held7over on 2013-04-25
I tried making reading the perl script for a comment that would tip me off on this question but didn't find one. But I found something on a different web site referring to ddclient which answers my question and puts my worries back to sleep, although I am not using DynDns.org, but rather updating my Domain Host (NameCheap) directly with ddclient:

> The general rule is to not send updates to the dyndns servers more than once per fifteen minutes to be safe. If you abuse their free service they will delete your account. _**Keep in mind that the "daemon" directive in the ddclient.conf file is the amount of time ddclient will check your local IP. Ddclient will only contact dyndns if the IP changes.**_ If you set the "daemon" directive to one minute that will allow ddclient to look at your interface every minute. Only if the IP changes will ddclient make a connection to DynDns.org. You can of course force an update to dyndns with "ddclient -force" and this will send the IP even if it has not changed. Sending updates for an IP that has not changed is considered abusive.

So, if I am reading this correctly, ddclient will not abusely update my Domain Host, as it waits for my Dynamic IP to be changed by my ISP first. SO, I could have ddclient daemon checking my modem's status page every minute for such a external IP change and not be abusing my Domain Host. So, I think I am good. I hope this answers someone else's question also...

---


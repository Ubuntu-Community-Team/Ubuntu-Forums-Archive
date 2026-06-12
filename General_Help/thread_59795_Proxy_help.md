---
title: "Proxy help"
date: 2005-08-25
forum: General Help
---

### Post by masteryoda on 2005-08-25
I am a newbie to linux...
I have 2 pcs one with win xp and one with kubuntu/winxp
I have adsl over eth0 in kubuntu/winxp pc and I share this with my other pc thru eth1.  I need a proxy server to do this in kubuntu also. I have tried squid..but got confused with configuring  ](*,) ... plz tell me how to do it. 
I have also heard abt tinyproxy... but it has no documentation for using or configuring it.. 
plz help...

---

### Post by tonym on 2005-08-26
I've used squid for some time now I - it was easy enough to configure as the default file had plenty of info but its long enough ago that I can't be sure that I remember all the details.  From what I remember,  the only changes I made to the default config file were:

The port it listens on.

An access control list "ACL" to allow my local network full access.

I'm not near my machine at the moment so I can't post bits from my config.  Reply if you'd like me to over the weekend.

---

### Post by masteryoda on 2005-08-26
Thx for replying...
It will be great if you can post it over the weekend...
mean time i'll install it again, and try to configure it.

---

### Post by tonym on 2005-08-27
I can't attach my squid.conf as its too big.  However,  I started with the default file and changed / added the following:

```
http_port  80
```
```
acl localnet src 192.168.0.0/255.255.0.0
``` 
```
http_access allow localnet
```

Hope this helps.

---

### Post by masteryoda on 2005-08-29
Thx dude... it worked... I also installed webmin... it made configurations very easy... just like proxyplus in Win

---


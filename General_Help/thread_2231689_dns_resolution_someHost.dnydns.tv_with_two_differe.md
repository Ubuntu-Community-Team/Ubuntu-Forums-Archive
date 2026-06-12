---
title: "dns resolution someHost.dnydns.tv with two different IP's"
date: 2014-06-27
forum: General Help
---

### Post by arquint on 2014-06-27
Hi community
 My domain is [someHost.dyndns.tv]("http://someHost.dyndns.tv").
 When I hit the following commands on my linux box I don't get the same IP address back as expected.
 
host command:
  ```

$ host someHost.dnydns.tv
someHost.dnydns.tv has address 91.237.x.x

```

nslookup command
  ```

$ nslookup someHost.dyndns.tv
Server:     127.0.1.1
Address:    127.0.1.1#53
Non-authoritative answer:
Name:   someHost.dyndns.tv
Address: 178.198.x.x

```

So, normally I should get back the same IP even for the host or nslookup command. Why is this different in these queries?
 The reason for my question is that I use an sms gateway service and  they just accepts my hostname or ip. So, because I get assigned an IP  dynamically I can just go for the FQDN. But this does not work and  that's why I figured out the stuff I explained above.

---


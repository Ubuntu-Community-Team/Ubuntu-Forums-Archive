---
title: "exim paniclog - socket bind() to port 25 for address XXX.YYYY.ZZZ.QQQ failed"
date: 2017-03-07
forum: General Help
---

### Post by marchello_lippi2 on 2017-03-07
Hi all, 
Got this message today from "root": 

```

exim paniclog /var/log/exim4/paniclog on localhost.localdomain has non-zero size,
mail system might be broken. The last 10 lines are quoted below.

2017-03-07 05:13:34 socket bind() to port 25 for address XXX.YYYY.ZZZ.QQQ failed:
Cannot assign requested address: daemon abandoned
2017-03-07 05:22:03 socket bind() to port 25 for address XXX.YYYY.ZZZ.QQQ failed:
Cannot assign requested address: daemon abandoned
```

The ip address XXX.YYYY.ZZZ.QQQ was my old one, changed yesterday by my ISP. Receiving mail on my backup mx, so I did not lost any email and I am able to read it there. Changed dns record for my example.org domain already yesterday.
What should I change in exim4 settings now to receive mail normally?
Please advise.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty

---- 

Upd: Found and changed exim4 record
> 
/etc/exim4/update-exim4.conf.conf:dc_local_interfaces='127.0.0.1 ; ::1; XXX.YYYY.ZZZ.QQQ'                                                                                                                                                              
/etc/exim4/update-exim4.conf.conf:dc_relay_nets='127.0.0.1; XXX.YYYY.ZZZ.QQQ'


Ok, now my exim4 started to accept mail again 

Now when I start my exim4, it alerts about not empty panic log, but still it works. 

> 
sudo service exim4 start                                                                                                                                                                                           
 * Starting MTA                                                                                                                                                                                                                              [ OK ] 
ALERT: exim paniclog /var/log/exim4/paniclog has non-zero size, mail system possibly broken


Not sure if I should remove panic log manually..

---


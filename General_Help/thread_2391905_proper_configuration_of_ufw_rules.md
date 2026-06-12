---
title: "proper configuration of ufw rules"
date: 2018-05-14
forum: General Help
---

### Post by derekcentrico on 2018-05-14
Converting over from the apparently defunct PGL now that I'm clean install on 18.04.  I'm curious if these rules make sense to allow these IPs and ports or services.  I found examples where IPs were using insert #s and my understanding is that this would be useful when later I figure out how to block complete IP ranges from iblocklist and other source files.

Advice totally appreciated on best practice to get these allowed and to import iblocklist files to disallow the remainder that have no exception.


```
sudo ufw insert 1 allow from 192.168.1.0/24
sudo ufw insert 2 allow from 10.0.0.0/24
sudo ufw insert 3 allow from 52.6.162.203
sudo ufw insert 4 allow from 70.90.57.121 
sudo ufw insert 5 allow from 239.255.255.250 
sudo ufw insert 6 allow from 50.253.170.34 
sudo ufw insert 7 allow from 196.54.41.7 
sudo ufw insert 8 allow from 108.181.57.1 
sudo ufw insert 9 allow from 196.52.2.33 
sudo ufw insert 10 allow from 218.215.42.95 
sudo ufw insert 11 allow from 196.52.39.28 
sudo ufw insert 12 allow from 151.227.34.125 
sudo ufw insert 13 allow from 59.167.95.34 86
sudo ufw insert 14 allow from 123.207.225 
sudo ufw insert 15 allow from 188.233.197.10 
sudo ufw insert 16 allow from 184.168.26.1


sudo ufw allow 3900:65534/tcp
sudo ufw allow 3900:65534/udp
sudo ufw allow http
sudo ufw allow https
sudo ufw allow nfs
sudo ufw allow 22
sudo ufw allow 53
sudo ufw allow 443
sudo ufw allow 500
sudo ufw allow 900
sudo ufw allow 922

```

---


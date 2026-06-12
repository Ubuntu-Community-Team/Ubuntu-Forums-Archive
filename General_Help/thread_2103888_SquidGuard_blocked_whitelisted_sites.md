---
title: "SquidGuard blocked whitelisted sites"
date: 2013-01-11
forum: General Help
---

### Post by CyberJacob on 2013-01-11
Hi all,
I'm trying to set up a whitelist in squidguard so that all unlisted sites get blocked. I have the following line in my squid.conf
```
url_rewrite_program /usr/bin/squidGuard -c /etc/squid3/inbound/squidGuard.conf
```
and this in url_rewrite_program /usr/bin/squidGuard -c /etc/squid3/inbound/squidGuard.conf
```
dbhome /var/lib/squidguard/inbound/db/blacklists
logdir /var/log/squid3/inbound

dest auth{
        urllist         auth/urls
        log verbose     squidGuard-full.log
}

dest facebook{
        domainlist      facebook/domains
        urllist         facebook/urls
        log verbose     squidGuard-full-fb.log
}

acl {
        default {
                pass auth facebook none
                redirect        http://172.20.0.1/incoming.php
                log verbose     squidGuard-full.log
        }
}

```
However [www.facebook.com/dialog/oauth](www.facebook.com/dialog/oauth) is still blocked, even when I have both [www.facebook.com/dialog/](www.facebook.com/dialog/) and [www.facebook.com/dialog/oauth](www.facebook.com/dialog/oauth) in /var/lib/squidguard/inbound/db/blacklists/facebook/urls
I have run squidGuard -C all as the proxy user, however this has not resolved the issue. Running the following also confirmes that the site is blocked
```
root@Proxy1:~# echo "http://www.facebook.com/dialog/oauth? 1.2.3.4/- user GET -" | squidGuard -c /etc/squid3/inbound/squidGuard.conf -d
2013-01-11 14:54:44 [7004] New setting: dbhome: /var/lib/squidguard/inbound/db/blacklists
2013-01-11 14:54:44 [7004] New setting: logdir: /var/log/squid3/inbound
2013-01-11 14:54:44 [7004] init urllist /var/lib/squidguard/inbound/db/blacklists/auth/urls
2013-01-11 14:54:44 [7004] loading dbfile /var/lib/squidguard/inbound/db/blacklists/auth/urls.db
2013-01-11 14:54:44 [7004] init domainlist /var/lib/squidguard/inbound/db/blacklists/facebook/domains
2013-01-11 14:54:44 [7004] loading dbfile /var/lib/squidguard/inbound/db/blacklists/facebook/domains.db
2013-01-11 14:54:44 [7004] init urllist /var/lib/squidguard/inbound/db/blacklists/facebook/urls
2013-01-11 14:54:44 [7004] loading dbfile /var/lib/squidguard/inbound/db/blacklists/facebook/urls.db
2013-01-11 14:54:44 [7004] squidGuard 1.4 started (1357916084.639)
2013-01-11 14:54:44 [7004] squidGuard ready for requests (1357916084.641)
2013-01-11 14:54:44 [7004] source not found
2013-01-11 14:54:44 [7004] no ACL matching source, using default
2013-01-11 14:54:44 [7004] Request(default/none/-) http://www.facebook.com/dialog/oauth 1.2.3.4/- user GET REDIRECT
http://172.20.0.1/incoming.php 1.2.3.4/- user GET
2013-01-11 14:54:44 [7004] squidGuard stopped (1357916084.641)
root@Proxy1:~#
```

Any ideas why the site is still blocked?

Thanks!

---


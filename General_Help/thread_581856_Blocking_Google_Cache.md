---
title: "Blocking Google Cache"
date: 2007-10-19
forum: General Help
---

### Post by Madstone on 2007-10-19
I  have Dansguardian, Tinyproxy, and Firehol setup for a transparent proxy for my son's PC however he can still see pages if he clicks on Google's Cache option (he hasn't done it yet I am just testing the configuration).
I don't want to block Google because obviously it serves a good purpose but I need to block that cache option.

Any ideas will be appreciated.

Just upgraded to Gutsy Gibbon 7.10 on his PC

---

### Post by Madstone on 2007-10-20
Hopefully this will help someone else...

After playing around with the bannedsitelist file in Dansguardian I decided to include the IP address that Google uses for the cache.

For example whenever I click on the Cache option the url seems to point to the same IP address everytime so I just placed it in the file I just mentioned and that seems to work like a charm.  Not sure if that address will remain the same over time but I will check it every now and then.

[http://64.xxx.xxx.xxx/cache:websitehere.com](http://64.xxx.xxx.xxx/cache:websitehere.com)

---


---
title: "Help Completely Removing and Reinstalling OpenSSL"
date: 2017-08-14
forum: General Help
---

### Post by chasidbase on 2017-08-14
I was having an error while trying to get a FreeRADIUS server running, so I followed the instructions [here]("https://lalitvc.wordpress.com/2014/06/26/freeradius-refusing-to-start-with-libssl-version-openssl-security-advisory-cve-2014-0160/"), which I think messed up my OpenSSL install.
After a bit of wrestling with "sudo apt-get remove openssl" and "sudo apt-get install openssl", I thought I had fixed it. However, I'm now getting errors with a PHP project, which made me suspect my OpenSSL install was to blame. 

"wget https://www.google.com" gives me
```
ERROR: cannot verify www.google.com's certificate, issued by ‘CN=Google Internet Authority G2,O=Google Inc,C=US’:
  Unable to locally verify the issuer's authority.
To connect to www.google.com insecurely, use `--no-check-certificate'.

```.

I think at this point I should probably completely remove OpenSSL from my system and reinstall it, but I don't know how to go about doing this. Any help would be appreciated.

---

### Post by chasidbase on 2017-08-16
Solved by first using "whereis openssl" and deleting everything I found. Then, using "apt-get install openssl". And then fixing my certificates with "apt-get install --reinstall ca-certificates" followed by running "update-ca-certificates". Everything works like a charm, now.

---


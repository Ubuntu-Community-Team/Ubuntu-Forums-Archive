---
title: "How to Troubleshoot Slow Network in Ubuntu?"
date: 2016-05-08
forum: General Help
---

### Post by weiqi3 on 2016-05-08
Hello,
I am posting this just want to get some general idea where can we check based on a slow network issue in Ubuntu.
For me, I may do the following :
1.use 'ethtool' to check speed & duplex issue;
2. ifconfig ==>check network interface, mtu
3. iftop ==> list all connection with its bandwidth use
4. traceroute ==> check route&#65279;

I will be really appreciated if more troubleshoot method can be raised!
ps. If a webpage simply timedout, what troubleshoot process should I follow?
Thank you guys so much!!!

---

### Post by HermanAB on 2016-05-08
Depends on what you mean by 'slow network'.

If you have a slow internet connection while browsing, then it can be due to a lame DNS.  You can look at the DNS addresses in /etc/resolv.conf and test them with dig.

---


---
title: "Squid3 Proxy on Ubuntu 12.04 LTS Server"
date: 2013-06-17
forum: General Help
---

### Post by rwestendorf on 2013-06-17
Hello forum, this is my first thread. I'm an assistant NA for a college and am configuring my first squid proxy on an Ubuntu server. I have set the server up and have squid running on the server. My issue is configuring squid to allow facebook and youtube with everything working. Currently the sites come up, but not everything works: ads and videos etc. For youtube the error is a flash issue. Ive configured squid.conf file with an acl to allow facebook.com and .facebook.com and an acl to allow youtube.com. Any help with this would be greatly appreciated. Thank you.

---

### Post by newbie-user on 2013-06-20
It sounds like you are whitelisting sites. You have to be very careful when using whitelists, since many ads and videos are linked from different sites. Can you post your squid.conf?

---

### Post by SeijiSensei on 2013-06-20
Remember, too, that the rules are evaluated in the order in which they appear in squid.conf.  You need to place all the whitelists ahead of any deny rules.

---

### Post by rwestendorf on 2013-06-20
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl facebook dstdomain .facebook.com
http_access allow facebook
acl youyube dstdomain .youtube.com googlevideo.com .ytimg.com
http_access allow youtube


Everything else is default setup. This is the only thing I have modified.

Thank you again

---

### Post by newbie-user on 2013-06-21
Your acl for youtube is misspelled. Aside from that, did you check that your whitelist is above your deny lines?

---

### Post by rwestendorf on 2013-06-21
The conf file is correct in Squid despite my thread misspell of youtube. The lines that I have added are above deny all.

---

### Post by HiImTye on 2013-06-21
.fbcdn.net is facebook's media domain

you might want to also whitelist fb.me and youtu.be

---

### Post by SeijiSensei on 2013-06-21
Take a look at /var/log/squid3/access.log or whatever it is called in Ubuntu.  Which connections are allowed and which are denied?

---

### Post by newbie-user on 2013-06-23
Have you tried running squid without the extra acl's? Just plain, default squid?

---


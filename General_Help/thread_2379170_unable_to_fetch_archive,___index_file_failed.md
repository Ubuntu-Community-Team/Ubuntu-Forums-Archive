---
title: "unable to fetch archive,   index file failed"
date: 2017-12-01
forum: General Help
---

### Post by Matrix01 on 2017-12-01
update did not go through

after ran update, error message : unable to fetch"

and ran sudo apt update again
index file failed,

any help?


[ATTACH=CONFIG]277713[/ATTACH]

[ATTACH=CONFIG]277712[/ATTACH]

---

### Post by Kirk Schnable on 2017-12-04
The URL it's trying to fetch is a dead giveaway (n135.network-auth.com???), I suspect that you're on some kind of network that has a captive portal to access the network (public WiFi?) and you're not logged in to the network or your session has expired.

So, the network is intentionally redirecting your Internet requests to a portal to try to get you to login.  This is breaking Apt because Apt can't find the data it is looking for, all it's getting is a portal login page and it doesn't know what to do with that.

Open a browser, do what you have to do to authenticate on the portal, and then try this action again.

---


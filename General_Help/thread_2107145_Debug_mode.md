---
title: "Debug mode?"
date: 2013-01-21
forum: General Help
---

### Post by MocroNL on 2013-01-21
Hey guys. Anyone know how to start bind9 in debug mode? It suddenly stopped working and I don't understand the errors that syslog is giving me. Tried to look it up on the net but no success.

tried: /etc/init.d/bind9 restart -d 

Obviously it did not work.

Many thanks.

---

### Post by Doug S on 2013-01-21
I am not aware of a debug level for bind9, only for named which would only apply if it actually starts.
 
Maybe post the errors here for some possible help from the community.
Also maybe try named-checkzone as described in the [troubleshooting section ]("https://help.ubuntu.com/12.04/serverguide/dns-troubleshooting.html")of the server guide, which does have a "-d" "enable debugging" option.

---


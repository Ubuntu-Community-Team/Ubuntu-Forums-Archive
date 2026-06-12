---
title: "Apache2 Bandwidth Quotas"
date: 2008-02-09
forum: General Help
---

### Post by discore on 2008-02-09
I have a server running Apache2 with some accounts on it and I want to put a quota on everyone's bandwidth usage. Some users have a domain hosted, and some only use /~username.

mod_throttle right? Nope, looks like it isn't supported in Apache2 and might not even be in development any more. I used to use mod_throttle's ThrottleUser directive and it was smart enough to handle everything.

It looked like mod_cband was the latest and greatest Apache2 quota mod, but as far as I can tell (and according to the documentation), the CBandUser directive only works inside of <VirtualHost>s. This doesn't work for accounts that use /~username exclusively.

My last idea is to setup [http://username.server.com](http://username.server.com) for every user and then rewrite /~username over to it. That way I can put CBandUser inside of the <VirtualHost> for username.server.com. That seems like it will work, but it really seems like there should be an easy way to put a quota on someone who uses /~username and I'm totally missing something.

Any ideas or comments on my possible solution? Thanks!

---


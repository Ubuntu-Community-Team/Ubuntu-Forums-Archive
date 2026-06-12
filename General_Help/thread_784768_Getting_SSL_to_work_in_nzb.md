---
title: "Getting SSL to work in nzb"
date: 2008-05-06
forum: General Help
---

### Post by Harksaw on 2008-05-06
So I'm trying to make an SSL connection using nzb, I can connect just fine if I don't check the "Use SSL" checkbox, but if I check that box it will say "SSL connection failed", nothing more elaborate than that. Also, when I start up nzb from a console it says 

"SSLfilter: unable to load unix openssl"

Does anyone know why this might be?

---

### Post by Harksaw on 2008-05-06
Someone in the irc.freenode.net #ubuntu told me to install the libssl-dev package. That made it work.

---


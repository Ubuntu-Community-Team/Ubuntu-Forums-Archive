---
title: "Connecting 2 Ubuntu servers to each other"
date: 2020-12-08
forum: General Help
---

### Post by yibos755 on 2020-12-08
I have 2 old office pcs which I downloaded latest ubuntu server release[COLOR=#141414][FONT=&quot](20.04.1 lts). And I want to connect each other so I can only have to ssh one of them and I can combine their hardware. [/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2020-12-08
Beowulf clustering is what you should look for. Depending on your load it may or may not be worth the effort.

One of those "sounds like a good idea".
But in practice more trouble than necessary or worth.

---

### Post by SeijiSensei on 2020-12-09
"Combine their hardware" for what purpose exactly? If it's only for file sharing, there are much easier solutions than building a Beowulf cluster like running NFS.  

By the ways, servers are generally not very CPU intensive so the gains from clustering for most services is pretty small.

As an example, I have a virtual server at Linode that provides mail and web services and runs both MySQL and PostgreSQL. It has a load average of about 0.05. The laptop I'm using at the moment has a load average ten times that.

---


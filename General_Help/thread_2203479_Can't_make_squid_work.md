---
title: "Can't make squid work"
date: 2014-02-03
forum: General Help
---

### Post by TheNomad on 2014-02-03
I am running on a very bare bones servers, It is a VPS with a fractional cpu and single network interface. Not to mention 256MB of memory, burstable to 512. I Just installed squid 3.1.19, moved the default conf file out of the way and put only two lines in the config file, which are:

http_access allow all
http_port 3128    


then restarted squid. ow whichever site I want to go, using google chrome on my laptop (running win XP) which is sitting behind a series of corporate firewalls, nature of which is unbeknownst to me. I am getting "ERROR The requested URL could not be retrieved" message. 

According to my understanding, this config file is equivalent of not running the proxy server. What am I doing wrong here, can anyone tell ?
Thanks

---


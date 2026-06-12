---
title: "Apache suddenly is extremely slow"
date: 2014-08-12
forum: General Help
---

### Post by suxipo2 on 2014-08-12
Hi everyone,

I have a VM Ubuntu 12.04 LTS with 3 cores, 8 GB RAM web server with maximum of few hundred visitors a day at peak time. I have Apache2, PHP, MySQL, Tomcat, Postgre, Webmin installed. Everything had been working fine until the past few days. All websites on Apache have become extremely slow that takes at least 5 min just to finish loading homepage. Even a simple hello world html file takes same amount of time to load. This happens whether I access from outside or inside the LAN. System load is not even high; still plenty of free RAM available. Rebooting Apache service or even rebooting the entire system doesn't help. Changing to another port, such as 8090, doesn't help either. All other services, however, such as Tomcat's websites, SSH, Webmin, show no problem or delay whatsoever.

All this makes me think the problem must be Apache but can't see why.

 Any idea on how I can troubleshoot this? 

Any tip is greatly appreciated.

Thank you very much in advance.

---

### Post by JetStorm on 2014-08-12
Check for something irregular in the error log (also in the php error log if it's separate).

---

### Post by SeijiSensei on 2014-08-12
Is DNS resolution working correctly on the server?

---

### Post by suxipo2 on 2014-08-12
> **JetStorm said:**
> Check for something irregular in the error log (also in the php error log if it's separate).

I found nothing unusual in the error.log, just a bunch of missing files, nothing special

> **SeijiSensei said:**
> Is DNS resolution working correctly on the server?

DNS shouldn't be the problem because the slow response also happens when accessing it through IP. And the fact that all other websites like Tomcat's and Webmin (using different webserver and ports) are fine means DNS shouldn't be the cause.

After messing around with some Apache's configuration like MaxClients, ServerLimit, restart machines,... the problem seemed gone away for few seconds and came back and stayed. I was fed up and gave up. HOWEVER, this morning the problem seems magically gone and the server is back to normal. 

No idea why but I am so glad it's working ok again

---


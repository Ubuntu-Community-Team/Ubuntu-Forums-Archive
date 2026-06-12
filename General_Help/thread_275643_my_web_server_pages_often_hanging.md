---
title: "my web server pages often hanging"
date: 2006-10-11
forum: General Help
---

### Post by don7777 on 2006-10-11
Hi,

I'm very new to system administration and I don't know where to start to track down this problem. So, any suggestions are greatly appreciated.

My machine is running Ubuntu 6.06. I installed apache2 and SSL and I'm trying to run appached through https. I'm running request-tracker (RT) which uses postgres to store and retrieve data. 

Whenever I connect to the machine from my local network, it works great.

Often when I connect to the machine from outside my network, pages hang.

I'm not sure where to start. I've looked in /var/log/apache2/*.log and there does not seem to be any problems. 

Where else should I look? Is there a way to increase the logging output from apache2 and postgres?

Thanks for any help,
Don

---

### Post by Endwin on 2006-10-11
A problem might be that if you are acessing a site on a home network you have A. a lot of hops to get there, and B. limited upload bandwidth. You can try and track down the bottleneck by using traceroute.

---


---
title: "Equivalent of Systemctl in 14.04"
date: 2017-06-24
forum: General Help
---

### Post by SnuKies on 2017-06-24
I've been following this [tutorial]("https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04") and I reached the step where I have to use ```
[COLOR=#3A3A3A][FONT=monospace]sudo systemctl daemon-reload , [/FONT][/COLOR][COLOR=#3A3A3A][FONT=monospace]sudo systemctl start tomcat, [/FONT][/COLOR][COLOR=#3A3A3A][FONT=monospace]sudo systemctl status tomcat[/FONT][/COLOR]
``` for Tomcat.
For what I've been reading on internet, systemctl is outdated and I can't use it anymore.

What would be the equivalent of those 3 commands?

---

### Post by howefield on 2017-06-24
How about this tutorial on the same website and subject except that is for 14.04 ?

[https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-14-04)

---

### Post by The Cog on 2017-06-24
I don't think systemctl is outdated. On the contrary, it's quite recent and replaces other things. 

I don't have tomcat installed here, but you could try **sudo service tomcat start**, and **sudo service tomcat status**. I think service was a command for upstart, which was replaced by systemd, and which itself replaced the init.d startup system. In the old init.d system the command would have been something like **/etc/init.d/tomcat start** and **/etc/init.d/tomcat status**

---

### Post by SnuKies on 2017-06-24
> **howefield said:**
> How about this tutorial on the same website and subject except that is for 14.04 ?

[https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-14-04)


Initially I followed that tutorial, but when I returned and google it, it returned that tutorial.

Thanks,

---

### Post by howefield on 2017-06-24
> **SnuKies said:**
> ...Thanks,

Cool, you are welcome.

---


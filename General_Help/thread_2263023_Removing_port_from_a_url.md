---
title: "Removing port from a url"
date: 2015-01-28
forum: General Help
---

### Post by mitchell14 on 2015-01-28
Hey guys,

I've been looking around trying to find a solution for what i am trying to achieve, however i haven't found anything so my last resort is to post on the forums.

What i'm after is some form of removing the port from url's i'm hosting on my VPS. So i have setup Virtual servers which are all working because i can access phpymyadmin via phpmyadmin.domain.com.

However i'm after a way of removing the port for things such as webmin, so instead of webmin.example.com:10000 i would like to have webmin.example.com.

If someone has a solution much would be apprectiated. 

Regards,
Mitchell

---

### Post by CharlesA on 2015-01-29
That would be a bad idea (imo), but if you really want to do that, you'll have to configure each service to list on a specific port and that could get messy, even with subdomains.

For webmin see here: [http://doxfer.webmin.com/Webmin/WebminConfiguration#Changing_the_port_and_address](http://doxfer.webmin.com/Webmin/WebminConfiguration#Changing_the_port_and_address)

---


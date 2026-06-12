---
title: "Apache Virtual Host Issue"
date: 2008-04-04
forum: General Help
---

### Post by IncomingFire on 2008-04-04
This is the first time I've tried to host multiple domains at the same ip.  So after much fiddling I finally got it to work....kind of...

<VirtualHost *>
DocumentRoot "/var/www/somedirectory"
ServerName somedomain.com
<Directory "/var/www/somedirectory">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

This works just fine on my local box....but when I go to another computer and bring up somedomain.com ... the browser gets redirected to the localhost of that box... hehe funny.

Couldn't find a solution yet, hopefully someone can help.

Thanks.

---

### Post by leg on 2008-04-04
That is probably because the other computer doesn't recognise the domain name and gives you its default host. I am not sure if this is the correct answer but you may need to add the host name into /etc/hosts so that you can find it on your network from a different computer.

Hope this helps.

---


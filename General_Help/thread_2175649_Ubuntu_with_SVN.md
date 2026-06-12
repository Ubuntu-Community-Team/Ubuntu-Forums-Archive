---
title: "Ubuntu with SVN"
date: 2013-09-20
forum: General Help
---

### Post by chris122 on 2013-09-20
hi guys, i clone an Ubuntu machine with SVN installed and hosted by Apache2.

I restore it to a  PC, but i have this error on apache logs:_** Invalid method in request \x16\x03\x01**_
Any ideas on how to solve this error?

I had already reconfigured the IP Address on ports.conf and on Virtual host config file.

Please help guys, i'm scratching my head on this.

Thanks in advance.

---

### Post by chris122 on 2013-09-20
any help guys :)

---

### Post by bkline on 2013-09-20
You might want to take a look at this:

[http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01)

---

### Post by chris122 on 2013-09-20
> **bkline said:**
> You might want to take a look at this:

[http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01)

i've tried that one already, i'm suspecting my apache settings is okay only the Subversion side, but I don't how to troubleshoot the subversion settings.

any ideas how to get started?

Thanks.

---

### Post by chris122 on 2013-10-08
problem solve guys, i set the IP Address to the same IP Address of the cloned server and it works fine.

i'm suspecting the IP Address is also tagged to the self signed cert on Apache settings.

---


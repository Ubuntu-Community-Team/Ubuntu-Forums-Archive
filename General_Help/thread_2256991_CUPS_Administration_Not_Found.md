---
title: "CUPS Administration Not Found"
date: 2014-12-16
forum: General Help
---

### Post by jack120 on 2014-12-16
Hi everyone, 

I have finished installing CUPS. But I'm having a problem with the web interface. 

If I go to [http://localhost:631](http://localhost:631), I am welcomed by the CUPS 1.7.2 Home page. My problem is that all of the links on this page return 'Not Found' when I select them. 

It seems odd and I can find little information about this. 

My cupsd.conf is quite different to the default, but it has been configured to allow the local machine access the admin page and no others. 

Thanks in advance everyone. 

Jack

---

### Post by ajgreeny on 2014-12-16
Have you tried restoring the original **cupsd.conf** if you have it, to see if that then allows you to access the links.

---

### Post by jack120 on 2014-12-17
Thank! I'll give it a try and see what that produces.

---


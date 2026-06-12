---
title: "Unable to obtain site identification status"
date: 2020-07-22
forum: General Help
---

### Post by knight69 on 2020-07-22
With the latest update to Ubuntu, I am no longer able to access my website server through Firefox. I don't know if this is a Firefox issue or a server issue. I can access the site through Chrome and older versions of Ubuntu/Firefox.  I can also access the site from cell phones and tablets running Firefox on Android. When I try to access the site from my desktop, Firefox times out with the error message "The connection has timed out". In preferences->privacy&security->certificates, there is no certificate stored and when I click on "get certificate" it times out with the message "Unable to obtain identification information for this site". There are no error messages in either case. 

I can view the site's certificate through chrome. The certificate is automatically renewed every three months and is presently valid until Oct. 22, 2020.

I have posted this problem on the Mozilla/Firefox forum but have received no replies. If anyone has any ideas, I would greatly appreciate it.

---

### Post by TheFu on 2020-07-23
Just a guess, but recent Firefox started using DoH for DNS. There should have been a prompt to accept/reject that change.

---


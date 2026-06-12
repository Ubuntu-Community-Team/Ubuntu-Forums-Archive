---
title: "Evolution SMTP Port Change?"
date: 2008-03-03
forum: General Help
---

### Post by Recked on 2008-03-03
Hello,

My isp requires a specific port be used for outgoing SMTP email. I have gone through Evolution a few times now and don't see where I can change the outgoing port?

Is there a way to do this?

Thank you

---

### Post by plucky on 2008-03-03
> My isp requires a specific port be used for outgoing SMTP email
Is there a way to do this?


When specifying the server name i.e **smtp.isp.com** you then need to add the port number after the name with a **:number**

So Open **Evolution > Preferences > Select Account > Edit > Sending email** Under server name put ```
smtp.isp.com:465
``` to use port 465 for Smtp mail server.


Good luck

---

### Post by Recked on 2008-03-03
Thanks very much Plucky. Didn't know you could do that kind of thing.

---


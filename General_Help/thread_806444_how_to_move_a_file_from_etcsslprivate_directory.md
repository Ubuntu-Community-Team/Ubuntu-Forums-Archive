---
title: "how to move a file from /etc/ssl/private directory"
date: 2008-05-24
forum: General Help
---

### Post by vpsubramanian on 2008-05-24
Hello!

I accidently moved smtpd.crt file to /etc/ssl/private instead of /etc/ssl/certs. Does that affect the email functionality in anyway and if so, how do I move it back to correct directory? I am unable to access the private directory.

TIA

Mani

---

### Post by Monicker on 2008-05-25
Which email functionality are you referring to?  Most likely it depends on the configuration of the mail server and where it expects the files to be.  Moving it is easy enough.

```
sudo mv /etc/ssl/private/filename /etc/ssl/certs
```

---


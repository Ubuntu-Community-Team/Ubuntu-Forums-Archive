---
title: "Timeout in sending Evolution email"
date: 2007-11-03
forum: General Help
---

### Post by buntuboy on 2007-11-03
Hi!

I am new in these forums and have just installed Ubuntu 6.10 on my laptop.  I am fairly familiar with Linux/Unix and can read/open/edit configuration files but have not done this in a while.

I am having a problem with not being able to send messages due to a timeout error.  I am able to ping the smtp server and even able to download mail so I believe it is just some configuration bug causing this.

If you could point me to the right config files or how-to docs that would be great.

Thanks.

---

### Post by ricster on 2007-11-06
having same problem on 7.04 but only when sending attachments, not large ones either, e.g. 50k or so.

---

### Post by dcstar on 2007-11-06
> **buntuboy said:**
> Hi!

I am new in these forums and have just installed Ubuntu 6.10 on my laptop.  I am fairly familiar with Linux/Unix and can read/open/edit configuration files but have not done this in a while.

I am having a problem with not being able to send messages due to a timeout error.  I am able to ping the smtp server and even able to download mail so I believe it is just some configuration bug causing this.

If you could point me to the right config files or how-to docs that would be great.

Thanks.

You first need to test basic connectivity by:

```
telnet smtp-server-name 25
```

If you get a response straight away from the SMTP server, then your system's connectivity is ok, if not then you are experiencing the same problem Evolution encounters.

---


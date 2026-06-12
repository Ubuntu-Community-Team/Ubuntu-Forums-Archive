---
title: "HTTPS connection failures"
date: 2005-10-30
forum: General Help
---

### Post by dizzy1234 on 2005-10-30
My browser is refusing to connect to anything using HTTPS protocol - it's not producing an error, it's just sits there doing nothing. FTP and HTTP are both fine. Any idea why this might be?

---

### Post by suRoot on 2005-10-31
```
telnet www.whatever.com 443
```

What kind of output does that produce?

Do you have a firewall in front of you?

---

### Post by dizzy1234 on 2005-10-31
[HTML]trying 70.168.53.226...[/HTML]

I think I am behind a firewall - I'm also using wireless if that might affect things

We had a power cut yesterday that affected everything, including the router / server, but it was working before that.

By the way, SSH and FTP aren't working either (I thought FTP was before but I was wrong)

---

### Post by suRoot on 2005-10-31
Talk to whomever controls your firewall & make sure the following TCP ports are open:

443 (ssl)
21 (ftp)
22 (ssh)

---


---
title: "can't access email with guarddog"
date: 2008-05-01
forum: General Help
---

### Post by Despot Despondency on 2008-05-01
Hey,
    I've just installed guarddog and it seems to be working fine. I just need a little help with the mail settings. At the moment I can't access any of my email accounts. I've enabled SMTP and POP3 on the internet zone, but it's still not working. Any ideas? Thanks in advance.

---

### Post by kellemes on 2008-05-01
> **Despot Despondency said:**
> Hey,
    I've just installed guarddog and it seems to be working fine. I just need a little help with the mail settings. At the moment I can't access any of my email accounts. I've enabled SMTP and POP3 on the internet zone, but it's still not working. Any ideas? Thanks in advance.

Section Mail..
- IMAP
- NNTP (for usenet)
- POP3
- POP3S
- SMTP

---

### Post by Despot Despondency on 2008-05-01
ok, so do I have to enable all of these? I've done that but it's still not letting me access my emails.

---

### Post by Despot Despondency on 2008-05-01
Sorted it out now. Apparently I needed HTTPS enabled in the file transfer section. Basically enabled everything and then eliminated things one by one until I found the necessary protocol.

---

### Post by kellemes on 2008-05-01
> **Despot Despondency said:**
> Sorted it out now. Apparently I needed HTTPS enabled in the file transfer section. Basically enabled everything and then eliminated things one by one until I found the necessary protocol.

Indeed that's how I do it often.. ;-)
Glad it works.

---


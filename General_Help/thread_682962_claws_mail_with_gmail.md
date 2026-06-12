---
title: "claws mail with gmail"
date: 2008-01-30
forum: General Help
---

### Post by ironjawedangel on 2008-01-30
Hello everyone,
I'm new to the forum and to ubuntu as well. I normally used and loved incredimail so I downloaded claws because they seemed similar. I saw some posts about problems as well, I tried changing the ports, but nothing works. Everytime I try to check new mail it says that "Error occurred while processing mail" I can send mails but i cannot receive them. Does anyone has suggestions? Or is it a better program than claws mail. I looked at thunderbird and evolution but i don't like them as much as claws. Also please keep in mind that I'm not very used to use commands.
Thanks.:confused:

---

### Post by bks on 2008-01-30
Go into your account settings and enable SSL on the POP3 server and change the port to 995. That what I had to do with my GMail. I used Thunderbird, but the server settings should all be the same.

---

### Post by ironjawedangel on 2008-01-30
I guess it's something about certificates, because everytime it tries to connect, it says that the certificate is unknown.

---

### Post by sofiankrt on 2008-04-14
I use Claws Mail as well, with Gmail. But I'm having a problem with sending emails? It says that it can't "queue" the file for sending, but that's probably because I removed the Gmail/Queue label. I'll see what happens if I redo that...
But I'm getting emails perfectly, on IMAP. Just make sure you have the enable IMAP box thing checked from Settings in the Gmail interface, and set the port to... 993, on SSL, I think.
Tell me if it helps.

---

### Post by Skorzen on 2008-06-11
I don't want to open a new thread so I'll write just right here anyway.

I'm currently trying Claws Mail 3.4.0 but I can't get my e-mails from Gmail.

```
SMTP port = 587
POP3 port = 995
POP3 uses SSL and SMTP doesn't. Instead, SMTP uses STARTTLS.
```

I can send e-mails but can't load the ones from Gmail server.

Any suggestions?

---


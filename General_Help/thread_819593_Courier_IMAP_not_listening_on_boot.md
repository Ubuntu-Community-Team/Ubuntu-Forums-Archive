---
title: "Courier IMAP not listening on boot"
date: 2008-06-05
forum: General Help
---

### Post by sunstriker on 2008-06-05
Hi,

So I'm running a postfix/fetchmail/courier/squirrelmail config for a while now. Now I wanted to connect to the imap server using a mail client from my laptop, because I don't use squirrelmail a lot.
I saw that Courier was only listening on localhost. Which is perfectly normal. I edited the etc/courier/imapd file into this:

```
PORT=127.0.0.1.143,192.168.2.5.143
```

If the comments in the imapd file are right. This would make courier listen on both ip's on port 143. The weird thing is that I have to do a force-reload every time I reboot on the courier-imap daemon before it starts listening on 192.168.2.5.
any ideas why this happens? Am I doing something wrong?

---

### Post by sunstriker on 2008-06-06
Nobody has a clue? :(

---

### Post by colo on 2008-06-06
Care to post a log excerpt of your bootup process?

---


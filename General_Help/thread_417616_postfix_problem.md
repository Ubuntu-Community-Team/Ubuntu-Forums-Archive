---
title: "postfix problem"
date: 2007-04-21
forum: General Help
---

### Post by jmvidalvia on 2007-04-21
I have postfix and mailx working.
I have a LAN with a server (hostname: server) (192.168.1.20) and my laptop (hostname: laptop) (192.168.1.25)
From server, I do:

```
mailx usr_a@server
``` 

and I get an e-mail in server box for user user_a.

```
mailx account@gmail.com
```

and I get an e-mail in my gmail account

But I do:

```
mailx usr_b@laptop
```

and it doesn't work. I also tried:

```
mailx usr_b@192.168.1.25
```

with no success. The message I get is:

```
Final-Recipient: rfc822; usr_b@laptop
Action: failed
Status: 5.4.4
Diagnostic-Code: X-Postfix; Host or domain name not found. Name service error
    for name=server type=AAAA: Host not found

```

If I ping laptop form server, I get a response, and viceversa.

If I try from laptop to server, it happens the same.
**So, I cannot send e-mails within my LAN**.

My question is: ¿how can I send a mail to a different machine in my LAN?
Thanks a lot!

---

### Post by howlingmadhowie on 2008-04-27
i have exactly the same problem

i think it's because the computer is querying the dns on the router, but i'm not sure.

---


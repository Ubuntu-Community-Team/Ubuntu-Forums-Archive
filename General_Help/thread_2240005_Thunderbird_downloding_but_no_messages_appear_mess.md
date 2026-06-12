---
title: "Thunderbird downloding but no messages appear messages."
date: 2014-08-17
forum: General Help
---

### Post by rsteinmetz70112 on 2014-08-17
I have a problem downloading messages with Thunderbird. The POP3 download starts as expected at some point new messages stop appeariong in the inbox, although Thnderbird reports reports many messages are left to be downloaded. Checking netstat I can see the connection to the server it is the only active connection. Using system monitor I can see the downlaod is continuing . But no new messages appear in teh Inbox. I have allowed the downlaod to continue for long lengths of time download in hundress of megabytes.

---

### Post by lisati on 2014-08-17
There might be a message with a very large attachment waiting to be downloaded. Are you able to check your email via webmail?

---

### Post by dragonfly41 on 2014-08-17
pop3browser should also help you to view/clear any inbound mail through terminal commands

> Allows to check a pop3 mailbox before downloading any mail

---

### Post by SeijiSensei on 2014-08-17
Try this:

```

$ telnet your.mail.server 110
[color=blue]Connected to your.mail.server
+OK[/color]
user yourusername
pass yourpassword
list
[...]
quit

```
Items in blue are server responses.

That will return a list of all pending messages with their associated sizes like this:
```

1 6017
2 15808
3 11204
4 24488
5 4998
6 41357
7 13618
8 13618
.

```

---

### Post by rsteinmetz70112 on 2014-08-25
Thanks for the suggestions but I'm still stuck. 

The POP3 account does have some messages with large attachments. I don't think that's the problems as some accounts have downloaded them just fine. I can telnet and get a list of messages. POP3 (dovecot) seems to be working fine.

---


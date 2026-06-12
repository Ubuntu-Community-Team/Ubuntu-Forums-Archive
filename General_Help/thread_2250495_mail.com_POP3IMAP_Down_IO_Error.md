---
title: "mail.com POP3/IMAP Down? I/O Error"
date: 2014-10-29
forum: General Help
---

### Post by vanessax on 2014-10-29
Since last night (2014 Oct 27) I haven't been able to connect to pop.mail.com or imap.mail.com.

I use Evolution and it was working fine the day before and suddenly stopped last night. Now I always get this error:

*"Could not connect to POP server pop.mail.com: Input/output error*"

Has anyone else noticed this problem?

PS: I tried both POP3 and IMAP, using the information at:
[http://www.emailquestions.com/mail-com/3632-what-pop-imap-servers-mail-com.html](http://www.emailquestions.com/mail-com/3632-what-pop-imap-servers-mail-com.html)

---

### Post by SeijiSensei on 2014-10-29
Works from here:
```

[root@mail ~]# telnet pop.mail.com 110
Trying 74.208.5.12...
Connected to pop.mail.com.
Escape character is '^]'.
+OK POP server ready H migmxus004 0M9ZXK-1XvuTf1dq3-00CNqN
^]
telnet> quit
Connection closed.

```

---

### Post by vanessax on 2014-10-29
Ok, I verified portscan and telnet work:

```

$ telnet pop.mail.com 110
Trying 74.208.5.12...
Connected to pop.mail.com.
Escape character is '^]'.
+OK POP server ready H migmxus005 0M8kWT-1XvirH305E-00CItN
user **********
+OK password required for user "**********"
pass **********
+OK mailbox "**********" has 2 messages (7526 octets) H migmxus005
get
-ERR unknown command
list
+OK
1 3545
2 3981
.
quit
+OK POP server signing off
Connection closed by foreign host.

```

BUT Evolution still gives me an "Input/Output Error" error message, I tried both the regular 110 port and the SSL 995 port and I get the same error. Is this a problem with Evolution?

But Evolution IS working with gmail through pop3.

---

### Post by SeijiSensei on 2014-10-30
Can't help with Evolution; I use Thunderbird.

---

### Post by vanessax on 2014-10-30
Suddenly after trying a hundred times, Evolution is working now, no more "Input/Output Error" and it downloads via pop now. Thanks everyone.

---


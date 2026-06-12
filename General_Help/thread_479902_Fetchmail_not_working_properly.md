---
title: "Fetchmail not working properly"
date: 2007-06-20
forum: General Help
---

### Post by GMWeezel on 2007-06-20
Whenever I try to use fetchmail to backup my GMail account, I get an error; note that my account name is #'d out.

```
fetchmail: POP3< 385 GmailId1088d98154faaf4f
fetchmail: POP3< 386 GmailId1089115ee5170c7d
fetchmail: POP3< 387 GmailId10892ea45715c43b
fetchmail: POP3< .
387 messages for ######## at pop.gmail.com (34136111 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 1829
fetchmail: POP3> RETR 1
fetchmail: POP3< +OK message follows
reading message #########@pop.gmail.com:1 of 387 (1829 octets)
Trying to connect to 127.0.0.1/25...connection failed.
fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
fetchmail: SMTP connect to localhost failed
fetchmail: POP3> QUIT
fetchmail: POP3< 
fetchmail: SMTP transaction error while fetching from ########@pop.gmail.com and delivering to SMTP host localhost
fetchmail: 6.3.6 querying pop.gmail.com (protocol POP3) at Wed 20 Jun 2007 06:49:13 PM CDT: poll completed
fetchmail: Query status=10 (SMTP)
fetchmail: normal termination, status 10

```

My fetchmail.rc file contains the following with my password X'd out.

```

poll pop.gmail.com with proto POP3 and options no dns
user '#########l' there with password 'XXXXXXXXXXXX' is james here options ssl
```

---

### Post by SimonHickling on 2007-06-22
It looks like it can't find your local Mail transport.  Fetchmail will deliver to a local mailserver which in your case it can't find.  Do you have sendmail, or postfix or some such installed and setup?

---

### Post by GMWeezel on 2007-06-22
Nope; I missed that in the article I read and that fixed it. thanks.

---

### Post by andrew.46 on 2007-07-05
Hi,

> **GMWeezel said:**
> Nope; I missed that in the article I read and that fixed it. thanks.

Have you had a look at the walkthrough that I wrote that describes all this in some detail:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 And of course you are missing procmail :-)

                  Andrew

---


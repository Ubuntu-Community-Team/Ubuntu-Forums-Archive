---
title: "Email broken in Hardy Heron"
date: 2008-05-25
forum: General Help
---

### Post by zcx2007 on 2008-05-25
Been running Gutsy successfully for months, using Evolution to pick up mail from ISP's POP server, and a local installation of postfix for outgoing mail.

Did the online upgrade to Hardy which went without incident.

Now Evolution cannot pickup mail 'Connection Refused'.

Cannot telnet to the POP server either; connection refused.

Wireshark shows that evolution's DNS lookup works fine, but then the Hardy makes no attempt to connect to the  POP server i.e. no SYN is sent.

So the 'connection refused' message is coming from inside Hardy.

Messages sent to postfix are not delivered; mailq shows 'connection refused'.  Wireshark shows again that postfix does the DNS lookup but then fails to connect to the destination MTA.

So it looks like there's something in Hardy that prevents outgoing connections to ports 110 and 25.

Web browsing and newsgroups work fine.

Any ideas?

zcx

---

### Post by zcx2007 on 2008-05-26
Fixed.

---


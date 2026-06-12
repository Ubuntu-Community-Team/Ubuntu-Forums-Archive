---
title: "Evolution - bounce email?"
date: 2006-08-05
forum: General Help
---

### Post by _simon_ on 2006-08-05
Is there anyway in Evolution to bounce email back so that the sender believes the address is invalid?

---

### Post by philippe_carlo on 2006-08-05
Nope. I'm very disappointed with evolution as an email client. Before switching to ubuntu, I was using the KDE desktop. Although it was bloated with functionality and sometimes kind of slow, at least this kind of features are available there. Evolution developers may want to take a look at kmail.

---

### Post by Whoopie on 2006-08-05
Hi,

look at [http://wiki.apache.org/spamassassin/ResendingMailWithHeaders](http://wiki.apache.org/spamassassin/ResendingMailWithHeaders)

> Evolution: Select the message. In the "Actions" menu, choose the "Forward" submenu (not "Forward message", the "Forward" submenu). Pick "Redirect", fill in the "To" field, and press "Send".

On Edgy, it's:

> Evolution: Select the message. In the "Message" menu, choose the "Forward As..." submenu (not "Forward message", the "Forward As..." submenu). Pick "Redirect", fill in the "To" field, and press "Send".

Best regards,
Whoopie

---

### Post by blurp on 2008-02-11
> **Whoopie said:**
> Hi,

look at [http://wiki.apache.org/spamassassin/ResendingMailWithHeaders](http://wiki.apache.org/spamassassin/ResendingMailWithHeaders)

Evolution: Select the message. In the "Actions" menu, choose the "Forward" submenu (not "Forward message", the "Forward" submenu). Pick "Redirect", fill in the "To" field, and press "Send".



I tried this and I got

> Your account does not have permission to use <xxx@yyy.zzz>
as a From address.

How do I solve this?

I'm using Gutsy / evolution 2.12.1.

---


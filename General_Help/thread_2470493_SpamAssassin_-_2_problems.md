---
title: "SpamAssassin - 2 problems"
date: 2022-01-01
forum: General Help
---

### Post by Anquietas on 2022-01-01
Hello,

I use Logwatch and it daily mails me about what happened on the server a day ago.
I have SpamAssassin with Amavis on Ubuntu Server with Dovecot and Postfix email software.

The first error that shows me is this: "spamd internal error, python traceback seen in response" - what is this about ?
The second error that shows me is this: "idle children more than 2 maximum idle children. decreasing spamd children:"

What can I do to resolve these ?

And most importantly: we receive and send a lot of important mails !
Can any of the above errors lead to the emails not being delivered ?

Thank you !

---

### Post by kasdanny on 2022-03-07
> **Anquietas said:**
> Hello,

I use Logwatch and it daily mails me about what happened on the server a day ago.
I have SpamAssassin with Amavis on Ubuntu Server with Dovecot and Postfix email software.

The first error that shows me is this: "spamd internal error, python traceback seen in response" - what is this about ?
The second error that shows me is this: "idle children more than 2 maximum idle children. decreasing spamd children:"

What can I do to resolve these ?

And most importantly: we receive and send a lot of important mails !
Can any of the above errors lead to the emails not being delivered ?

Thank you !

I too am having this same problem with spamd. No other details related that I can find in the logs. If you found a solution I would love to here it. In the mean time I am gonna turn all verbose logging on to try and narrow "mail spamd[...]: internal error, python traceback seen in response" error down...

---

### Post by Anquietas on 2022-03-08
I also have this problem: "    spamd: child [___] killed successfully: interrupted, signal ___ (___): 2 Time(s)" - what could be the problem ?

---


---
title: "postfix (outgoing) address rewrite depending on subject"
date: 2022-11-02
forum: General Help
---

### Post by sda100 on 2022-11-02
Can postfix be used to filter on the subject line of outgoing messages, and change the from/reply address accordingly?

---

### Post by TheFu on 2022-11-02
[https://www.postfix.org/ADDRESS_REWRITING_README.html](https://www.postfix.org/ADDRESS_REWRITING_README.html)

---

### Post by sda100 on 2022-11-02
Yes, I've had a skim through that but it's not evident to me that it can perform this logic: "if (subject) contains (some-text) then set 'From' header to 'some@address' "

---

### Post by SeijiSensei on 2022-11-03
Procmail can do this with its associated formail command, but procmail is a "mail delivery agent," not a "mail transfer agent" like postfix. You could create an email alias that directs any messages it receives to a "recipe" in procmail.  Procmail can test on criteria and act accordingly.You would then send any message you want to rewrite to the alias and have it send it out with altered headers on your behalf. See "man procmailrc" and "man procmailex" for details.

---


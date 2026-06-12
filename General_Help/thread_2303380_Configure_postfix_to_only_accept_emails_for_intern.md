---
title: "Configure postfix to only accept emails for internal addresses from local senders?"
date: 2015-11-18
forum: General Help
---

### Post by xxlray on 2015-11-18
I am migrating a sendmail mailserver to postfix. Previously I was able to use a regular expression to let the server only accept mails from local addresses for addresses that are marked as internal (inside the ldap tree). This tremendously(!) cut down on Spam for internal mailing lists.

 Does anybody know how to achieve the same for postfix? I tried postfwd but couldn't get it to work properly and the support is not answering my requests.

---

### Post by SeijiSensei on 2015-11-18
You can tell Postfix to consult a set of regex rules by adding:
```

smtpd_helo_required = yes
smtpd_helo_restrictions = check_helo_access pcre:/etc/postfix/helo_access

```
Then create /etc/postfix/helo_access and put your rules in there like this:
```

# no two-letter country-code domains except us/ca
/\.us$/                 OK
/\.ca$/                 OK
/\.[a-z][a-z]$/         REJECT US senders only

# various blacklists
/\.badsender\.net$/     REJECT

```
Anything after the "REJECT" is included in the bounce message, e.g., "US senders only".  Restart Postfix to make the changes active.

These rules apply to the identify of the sender server which is announced via the SMTP HELO command.  You can apply similar rules to the address in the From: field with the parallel "smtpd_sender_restrictions" ruleset.

I recommend reading this for more help and examples: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by xxlray on 2015-11-18
Thank you so much for the answer. I read a lot but didn't find this information. Probably I simply didn't come up with the correct buzz words. The examples you gave are about everything I need. I'll give it a try.

---


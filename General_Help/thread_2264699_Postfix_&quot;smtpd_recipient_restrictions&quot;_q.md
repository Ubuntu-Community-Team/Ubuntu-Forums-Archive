---
title: "Postfix &quot;smtpd_recipient_restrictions&quot; question"
date: 2015-02-09
forum: General Help
---

### Post by terryit3 on 2015-02-09
I am running Ubuntu 14.04.01 LTS using Postfix/Dovecot for a new mail server.

I have installed and configured Postgrey to try and halt some of the spam we get, but I would also like to use the built-in RBL in Postfix..

I have my /etc/postfix/main.cf modified as follows, and I just want confirmation that it's correct.

```
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,reject_rbl_client zen.spamhaus.org,reject_rbl_client bl.spamcop.net,reject_rbl_client cbl.abuseat.org,permit check_policy_service inet:127.0.0.1:10023
```

If anything is wrong, could you please post the corrected line I should be using?

Thanks!

---


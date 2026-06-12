---
title: "Helo command rejected: need fully-qualified hostname;"
date: 2012-11-05
forum: General Help
---

### Post by koszta on 2012-11-05
I have a mail server (postfix) and sending and receiving mail works no problem 99% of time.

I am using iRedMail package and I am getting an error when somebody from one particular server tries to send us mail. I always see:

```
 504 5.5.2 <info>: Helo command rejected: need fully-qualified hostname; from=<blabla@notworkingserver.com> to=<me@ourserver.com> proto=ESMTP helo=<info>

```

I have this set in main.cf file of my postfix:

```
smtpd_helo_restrictions = permit_mynetworks,permit_sasl_authenticated, check_helo_access pcre:/etc/postfix/helo_access.pcre

```

```
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unlisted_recipient, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_helo_hostname, reject_invalid_helo_hostname, check_policy_service inet:127.0.0.1:10031
```

how do I fix this so that we do not compromise the security of our postfix and yet be able to recieve email from them?

---


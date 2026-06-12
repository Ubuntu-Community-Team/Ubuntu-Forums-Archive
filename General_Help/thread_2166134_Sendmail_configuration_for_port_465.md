---
title: "Sendmail configuration for port 465"
date: 2013-08-07
forum: General Help
---

### Post by Joshua on 2013-08-07
I have a home server that used to send me some status emails with a basic sendmail configuration at externally hosted email accounts.  It looks like the ISP recently blocked port 25, and recommends using port 465.  Can anyone help me set that up?

With the old configuration, I would get errors that the connection timed out, and it seemed to take a very long time for that to happen when I sent test email.  After going into sendmail.mc and changing the "Port=smtp" settings to "Port=465" I got errors very quickly that the connections were just refused.  Not sure where to go from there.

---

### Post by Joshua on 2013-08-07
I should have shown the actual error I got:

```
$ sendmail -v user@domain.com
test
.
user@domain.com... Connecting to [127.0.0.1] via relay...
user@domain.com... Deferred: Connection refused by [127.0.0.1]
$
```

---

### Post by SeijiSensei on 2013-08-08
Changing the port sendmail listens on won't solve your problem.  You need to force sendmail to use port 465 outbound, and it needs to use TLS with certificates on that port.

This item might help:  [https://fedoraproject.org/wiki/Configure_sendmail_as_a_client_for_SMTPs](https://fedoraproject.org/wiki/Configure_sendmail_as_a_client_for_SMTPs)

---


---
title: "mail not sending to external email"
date: 2016-08-09
forum: General Help
---

### Post by Coder88 on 2016-08-09
(Note: I am trying to figure this out for a local Linux User Group, so any help here will be greatly multipled)

I want to be able to have the mail command send mail to an outside of my pc email address, e.g. [EMAIL="me@joogio.com"]me@joogio.com[/EMAIL]
I have sendmail and mailutils installed, the sendmail daemon is running, and I can send mail internally, e.g.
  $ sudo mail -s "Hello from root" joeuser
where i compose and ctrl+d to send the mail message to joeuser who then types
  $ mail
to see that internal mail.

But if i try to send mail not to joeuser but to [EMAIL="me@joogio.com"]me@joogio.com[/EMAIL] i never receive it at [EMAIL="me@joogio.com"]me@joogio.com
[/EMAIL]
My Thunderbird email for [email]me@joogio.com[/email] has server settings of IMAP port 143 and SMTP (outgoing email) port 587. I am wondering if somehow sendmail's daemon needs to be using port 587 to send mail instead of the default port 25 (most ISPs block port 25 I believe because of spam)? But if so, how do i configure that?

---

### Post by SeijiSensei on 2016-08-09
The first answer here tells you what you need to do to create a mailer that sends to port 587.

[http://unix.stackexchange.com/questions/132711/using-port-587-with-sendmail](http://unix.stackexchange.com/questions/132711/using-port-587-with-sendmail)

If you are blocked by your ISP, have you asked them whether there is a relay host you can use?  If so, you can add it to the "DS" in sendmail.cf like this:
```

DSprovider-relay.example.com

```
Now all outbound mail will be automatically forwarded to "provider-relay.example.com" for delivery.

---


---
title: "Problem with sendmail configuration"
date: 2023-06-26
forum: General Help
---

### Post by David_Partridge on 2023-06-26
I tried to change my sendmail configuration to use a different outbound smtp server and port.

I modified the last few lines of /etc/sendmail.mc to read:

```

nl # Masquerading options
FEATURE(`always_add_domain')dnl
MASQUERADE_AS(`perdrix.co.uk')dnl
FEATURE(`allmasquerade')dnl
FEATURE(`masquerade_envelope')dnl
dnl #
dnl # Default Mailer setup
define(`SMART_HOST', `smtp.ionos.co.uk')dnl
define(`RELAY_MAILER_ARGS', `TCP $h 465')dnl
define(`ESMTP_MAILER_ARGS', `TCP $h 465')dnl
define(`confAUTH_OPTIONS', `A p y')dnl
TRUST_AUTH_MECH(`EXTERNAL DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
FEATURE(`authinfo',`hash -o /etc/mail/auth/client-info.db')dnl
MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl

```

I then ran 

```
make sendmail.cf
service sendmail restart
```

I then looked in the journal and found:

sendmail[82759]: NOQUEUE: SYSERR(root): /etc/mail/sendmail.cf: line 71: unknown configuration line "465"

if I look at the file I see that line 71 just contains the text 465 

What do I need to fix please?

Thanks
David

---


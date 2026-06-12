---
title: "Certificate could not be verified..."
date: 2012-10-18
forum: General Help
---

### Post by AlexBooton on 2012-10-18
I get this message when trying to connect to the email server:

```
The server you are connected to is using a security certificate that could not be verified.

A certificate chain processed but terminated in a root certificate which is not trusted by the trust provider.

Do you want to continue using this server?
```

The users are on Windows using Outlook and Outlook Express.  In order to get these users to connect to the server I had to specify the SMPT server requires a secure connection (smtp port 995 instead of 110).

Other clients did NOT require the ssl connection.  Why some did and some did not is a mystery (to me).

The server (U12.04) is using postfix, dovecot, amavis, etc.  It is not using ispconfig.

I don't recall creating a certificate and did not subscribe to a certificate authority so I'm assuming the certificate was installed as part of the initial setup and is self signed.  I don't know how to verify this.

I googled and found some people had this issue when Cisco was involved.  That isn't the case here afaict.

Any ideas on how to fix this?

Thanks

---


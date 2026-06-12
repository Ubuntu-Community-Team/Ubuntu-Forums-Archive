---
title: "Accepting self-signed SSL certificate"
date: 2012-11-22
forum: General Help
---

### Post by holadebob on 2012-11-22
After more than a years use and up until this morning Binreader had no problem with a usenet server self-signed SSL certificate. Binreader is now refusing it. "SSL verification error: The root certificate of the certificate chain is self-signed, and untrusted"

No option comes up to accept it.

Do you know if this is a problem with Binreader or with Xubuntu? 

Can you tell me how to accept this certificate?

Thank you:confused:

---

### Post by MattBergholm on 2013-07-06
old thread, ever find a fix? I just ran into this error.

---

### Post by thermometer2 on 2014-05-02
**Option 1. Fairly simple workaround (this is what I did, as I insisted on using Binreader, because it can extract while downloading, which is AWESOME):**

Download and run stunnel. Configure it for your usenet server in stunnel.conf:

*; Usenet config*
*compression = zlib*
*[nttp]*
*accept = 127.0.0.1:119*
[I]connect = news.server.com:563
[/I]
Edit your usenet server's address into the last line, of course. Have Binreader connect to 127.0.0.1, on the normal (non-SSL) port 119, with your username and password. Stunnel will accept the connection (from Binreader to stunnel) and tunnel it to your usenet server over SSL. The only role stunnel really plays here is to *not* complain about a self-signed certificate, whereas Binreader *does*.

[B]Option 2. Possible solution:

[/B]If you can get your hands on the self-signed SSL certificate file, then you should be able to add it to your computer's list of trusted root certificates. This should stop Binreader complaining, although I never managed to pull it off myself.

---


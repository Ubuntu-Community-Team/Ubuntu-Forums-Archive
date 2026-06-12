---
title: "FTP error"
date: 2015-12-25
forum: General Help
---

### Post by scarecrow2 on 2015-12-25
Hi all first time posting but i am getting this weird error that i dont really see a solution to. This is on a VSFTPD server that uses a TLS connect. It used to work but even on a clean install of Ubuntu LTS it does this. What can i do to fix it?
 Here is the error:

```
Status:    Connecting to 10.0.1.147:21...
Status:    Connection established, waiting for welcome message...
Response:    220 (vsFTPd 3.0.2)
Command:    AUTH TLS
Response:    234 Proceed with negotiation.
Status:    Initializing TLS...
Status:    Verifying certificate...
Status:    TLS connection established.
Command:    USER gordon
Response:    331 Please specify the password.
Command:    PASS ********
Error:    GnuTLS error -15: An unexpected TLS packet was received.
Error:    Could not connect to server

```

Thanks!
(ps i just converted over to ubuntu from a windows server 2012 r2 environment so im a little bit of a scrub still)

################################EDIT#####################################
My FTP server on my windows server 2012 r2 environment works fine so i know that theoretically it is not a firewall issue.

---


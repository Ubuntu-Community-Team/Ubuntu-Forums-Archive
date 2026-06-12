---
title: "Google preventing use of ssmtp on 12.10 server"
date: 2013-01-01
forum: General Help
---

### Post by PaulWhipp on 2013-01-01
I've set up ssmtp on a 12.10 AWS server.

When I try to use it I get:
```
[<-] 220 mx.google.com ESMTP ni8sm27348605pbc.70
[->] EHLO footholdgame.com
[<-] 250 ENHANCEDSTATUSCODES
[->] STARTTLS
[<-] 220 2.0.0 Ready to start TLS
[->] EHLO footholdgame.com
[<-] 250 ENHANCEDSTATUSCODES
[->] AUTH LOGIN
[<-] 334 VXNlcm5hbWU6
[->] cGF1bC53aGlwcEBnbWFpbC5jb20=
[<-] 334 UGFzc3dvcmQ6
[<-] 535 5.7.1 https://support.google.com/mail/bin/answer.py?answer=78754 ni8sm27348605pbc.70
ssmtp: Authorization failed (535 5.7.1 https://support.google.com/mail/bin/answer.py?answer=78754 ni8sm27348605pbc.70)
```

Following [this thread]("http://ubuntuforums.org/showthread.php?t=1691878"), I found a message from google stating "suspicious sign in prevented".

Google's work around is that I should log in using a web browser. Unfortunately it's a server that has no GUI and I don't particularly want to clutter it up trying to add one just in order to get google to accept the emails.

Does anyone know how I can convince google that my sign on from this particular IP is legitimate without having to use a web browser on that IP?

---

### Post by PaulWhipp on 2013-01-01
Answering my own question from ongoing research:

[https://accounts.google.com/DisplayUnlockCaptcha]("https://accounts.google.com/DisplayUnlockCaptcha")

allowed me to open access and get the server enabled.

---

### Post by dcstar on 2013-01-02
> **PaulWhipp said:**
> Answering my own question from ongoing research:
.......
allowed me to open access and get the server enabled.

Then MARK the thread!

---


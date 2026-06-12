---
title: "nail and gmail"
date: 2008-02-29
forum: General Help
---

### Post by flightless bird on 2008-02-29
I've been trying to set up my /etc/nail.rc file to use the nail mail client with gmail (preferred so I can handle attachments), with no success. I can successfully use mailx to send plain mail, which I have configured with the following .mailrc file:
```

set smtp-use-starttls
set smtp=smtp://smtp.gmail.com:587
set smtp-auth=login
set smtp-auth-user=USERNAME@gmail.com
set smtp-auth-password=PASSWORD
set from="USERNAME@gmail.com (Flightless bird)" 

```

and after a bit of digging around in the man files and on the web came up with this for the /etc/nail.rc file:```
# Google
set smtp-use-starttls
set pop-use-starttls
set smtp-auth=login
set smtp=smtp.gmail.com:587
set pop=pop.gmail.com:996
set from=USERNAME@gmail.com
set smtp-auth-user=USERNAME@gmail.com
set smtp-auth-password=PASSWORD

```

which is basically the same, but while mailx works (using ssmtp) nail fiails with the following error message every time:```
 Error with certificate at depth: 0
 issuer = /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
 subject = /C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
 err 20: unable to get local issuer certificate
Continue (y/n)? could not initiate SSL/TLS connection: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
"/home/USER/dead.letter" 11/340
. . . message not sent.

```
Sorry for the long message, but any ideas/advice would be appreciated

Cheers

---

### Post by flightless bird on 2008-02-29
Don't worry about it -  tried mutt and it works out of the box, so to speak

---


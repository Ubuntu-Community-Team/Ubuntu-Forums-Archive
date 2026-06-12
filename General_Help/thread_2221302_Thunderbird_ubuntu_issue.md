---
title: "Thunderbird ubuntu issue"
date: 2014-05-01
forum: General Help
---

### Post by Darren_Rose on 2014-05-01
Started Thunderbird to get emails and this came up

[IMG]http://i868.photobucket.com/albums/ab250/RozzaMan/securityexception.png[/IMG]

Anybody tell me what it means?
Regards

---

### Post by TheFu on 2014-05-01
The DNS name for the website and the name on the certificate do not match. This is bad.

---

### Post by Darren_Rose on 2014-05-01
Thanks for your reply. Bad for me or bad for the provider?

Or both?

---

### Post by TheFu on 2014-05-01
Both.  Contact their support line.  It is strange for POP3 (unencrypted) to use SSL/TLS. If you were using POP3S (port 995), then I'd understand (and would NOT expect to see that error).

Look at the cert. Which domain is it?

---

### Post by Darren_Rose on 2014-05-01
Screen capture:
[IMG]http://i868.photobucket.com/albums/ab250/RozzaMan/certificate.png[/IMG]

Sorry to be a pain.

---

### Post by Darren_Rose on 2014-05-01
I notice that it was issued yesterday, may be something to do with that?

---

### Post by TheFu on 2014-05-01
The DNS location and the location listed by the certificate DO NOT MATCH!!!!!
Something is seriously wrong here.
* Your DNS is hijacked.
* Your ISP is stupid
* Your ISP email server settings have changed, but either you don't know it or they didn't tell you
* DO NOT TRUST this CERT!!!!

---

### Post by SeijiSensei on 2014-05-01
They have the same IP address:
```

$ host pop3.uwclub.net
pop3.uwclub.net has address 212.74.112.120
$ host pop3.tiscali-business.co.uk
pop3.tiscali-business.co.uk has address 212.74.112.80

```
Mismatched certificates for hosted services are not that uncommon.

I agree that it is unusual to see a certificate when connecting to plain old POP3 on port 110.

---

### Post by TheFu on 2014-05-01
No, they have different IPs - just the same subnet.  Major screw up by the email provider, IMHO.  Time to find a different email provider, definitely.

---

### Post by SeijiSensei on 2014-05-02
I must have misplaced my glasses!

---

### Post by Darren_Rose on 2014-05-02
Thanks guys. First port of call is to contact them ASAP then.

---


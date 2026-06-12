---
title: "Evolution App - will not accept port 993"
date: 2016-09-01
forum: General Help
---

### Post by kj.curry on 2016-09-01
Under Ubuntu 14.04 this email app (ver 3.10.4) will not configure its IMAP settings correctly.

When setting up IMAP - via Edit/Preferences/Mail Accounts/"accountname settings"/Receiving Mail/Configuration/... When setting the server port value. My ISP requirements are for port 993. This is selectable. BUT it will not save that value.

Attempts to check/refresh the server generate error message: "TCP connection reset by peer". Connection fails - no mail headers are transferred.

Upon returning to this dialogue box the (default) port value remains at 143. Multiple attempts made - not successful at getting the 993 value to stick.

Attempted to include ":993" at the end of the "servername" but this compounds the error by referencing the server as "servername:993:993".

Until I can resolve this concern my transition to Evolution is stuck.
[ :confused: Does that make me a Darwinist "transition to Evolution". Get it??? :confused: ]

Thanks in advance for your help and assistance.
Cheers
Kevin

---

### Post by mook765 on 2016-09-02
Maybe this is the reason:
[LIST]
[*]**Port 143** - this is the default IMAP non-encrypted port
[*]**Port 993** - this is the port you need to use if you want to connect using IMAP securely
[/LIST]
Encryption enabled ?

---

### Post by kj.curry on 2016-09-02
Greetings Mook765,

Yes thank you for that. I well aware of these port assignments. Thanks.

Re: Encryption enabled?
I swear to/at the gods of Kobol I went thru this a dozen times and test selected all three options numerous times after the initial settings failed.

On this occasion I selected the obvious:, "SSL on dedicated port". Boom! It worked.

Humbled yet again, but thanks for refocusing my brain.
Cheers
Kevin

---


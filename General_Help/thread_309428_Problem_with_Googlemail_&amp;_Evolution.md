---
title: "Problem with Googlemail &amp; Evolution"
date: 2006-11-29
forum: General Help
---

### Post by foofy on 2006-11-29
I'm having problems getting my Googlemail account setup with Evolution.

I got my account today and I've enabled the POP settings in Gmail, it even downloads my messages from my account, but when I try and send a test message I get the following error.

> Host lookup failed: smtp.googlemail.com : Name or service not known

I searched through the forums for help and tried many of the different account settings but I always get the same error.

Is anyone else having the same problem?
Is the SMTP sever down?
Can anyone help?

Many thanks, Chris :mrgreen:

---

### Post by arthursc on 2006-11-29
try pinging smtp.googlemail.com. I just did and got a response. use System/administration/network tools and use the ping. then try connecting to the via ip address. so replace smtp.googlemail.com with the ip adddress and see if that works. if it does then chances are you have a lookup problem.

here is the ip anyhow; 66.249.93.16

---

### Post by foofy on 2006-11-29
Still no joy

ping came back ok (IP 66.249.93.16) tried using that instead but got the same error.

Tried traceroute and it seams to get stuck at my ISP?

Maybe its a DNS problem?

Any ideas?

Thanks, Chris :confused:

---

### Post by mgmiller on 2006-11-29
They may have changed their mail server.  Just try gmail.com as the host name.  That is what I have the mail notifiction icon program set to use. I am also using pop.gmail.com in evolution and it works ok.

---

### Post by arthursc on 2006-11-29
sounds like your isp dns root cannot resolve. try telnet to host name on port 25 and see if you get an ehlo response

---

### Post by arthursc on 2006-11-29
my response from telnet smtp.googlemail.com 25
Trying 66.249.93.16...
Connected to googlemail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP j3sm4234621ugd

---

### Post by foofy on 2006-11-29
> **mgmiller said:**
> They may have changed their mail server.  Just try gmail.com as the host name.  That is what I have the mail notification icon program set to use. I am also using pop.gmail.com in evolution and it works ok.

I've changed all the addresses to gmail.com and the same old error.
Strangely the error message is still stating *smtp._googlemail_.com* not gmail.  Is this significant?

> **arthursc said:**
> sounds like your isp dns root cannot resolve. try telnet to host name on port 25 and see if you get an ehlo response

Ok I'd like to give this a try, but I have no idea what to do.  Could you talk me through it. :D

---

### Post by arthursc on 2006-11-29
aCLICK pplications/accessories/terminal

then type telnet smtp.googlemail.com 25

---

### Post by foofy on 2006-11-29
Ok I worked that out and this is what I got, but what does it mean?

> ~$ telnet smtp.googlemail.com 25
Trying 66.249.93.16...
Connected to googlemail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP h1sm21580637ugf

It just sat there for a while and did nothing.

---

### Post by arthursc on 2006-11-29
almost certainly now the email client. essentially you have connected to the server and resolved the hostname. so not sure why your not sending. 

It is 23:00 so I am off to bed. I maybe able to pick up on this tomorrow. Sorry to leave you in the dark...so to speak.

Hope someone can follow from here.

---

### Post by foofy on 2006-11-29
> almost certainly now the email client. essentially you have connected to the server and resolved the hostname. so not sure why your not sending.

It is 23:00 so I am off to bed. I maybe able to pick up on this tomorrow. Sorry to leave you in the dark...so to speak.

Hope someone can follow from here.

Thanks for all your help, sleep well, see you around tomorrow. :D

---

### Post by foofy on 2006-11-29
If it's any help I'm using Evolution 2.8.1.

Are there any known issues with it?

Is this the problem?

Many thanks, Chris. ](*,)

---

### Post by foofy on 2006-11-29
Well I don't know what I did but it works.

Must have been a server problem, or Jupiter was in retrograde.

I did scratch my head 13 times while looking into this...anyway.

Thanks for all your help.

Take care, Chris :-D

---


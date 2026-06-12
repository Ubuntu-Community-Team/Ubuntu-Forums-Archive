---
title: "Sending email in Evolution"
date: 2015-09-19
forum: General Help
---

### Post by grey1beard on 2015-09-19
While I have asked for help with the same problem before, my situation is different, and the solution will be, likewise.
While in UK, and with Easyspace as my ISP, I have no problems with my email setup.
Temporarily in USA, I have set up my laptop to run via a neighbour's network at first, via her Comcast cable TV, but now via my host's cable Comcast TV, now providing her with an internet package as well.

In both cases, I could not send email from my Evolution program. Receiving is fine. Using my Easyspace webmail keeps me in touch, receiving and sending, but I haven't been able to solve the Evolution problem, which I assume is down to not having the settings correct.

I've tried every combination available in the boxes, changing each in turn - SMTP, authentication or not, no encryption or SSL, checked supported types which gave PLAIN.
The only thing I haven't tried is changing my server from smtp.fan*****.co.uk to a comcast address, which I noted as a solution in a couple of google searches where comcast had been mentioned.

As I don't know if this is necessary (because I am now using a connection via Comcast) I'm here looking for help once again.

Regards all,
John

---

### Post by TheFu on 2015-09-19
Comcast blocks outbound port 25 except through their email relay. This is part of their anti-spam efforts.

What port are you connecting to Easyspace with SMTP over?  Common ports are 465/tcp and 587/tcp.  Hopefully, you are using IMAPS on 993/tcp for reading email.

---

### Post by grey1beard on 2015-09-19
Hi TheFu, and thanks for the quick response. 
With Easyspace, I have port 25 as default for SMTP, and POP on 110 :oops:
Regards
John

---

### Post by TheFu on 2015-09-19
> **grey1beard said:**
> Hi TheFu, and thanks for the quick response. 
With Easyspace, I have port 25 as default for SMTP, and POP on 110 :oops:
Regards
John

That explains it.  Server-to-Server SMTP is port 25.  Desktop-to-Server SMTP is not.  Use 465 or 587 for authenticated SMTP.  Most places use 465.

If you have ssh into the Easyspace box, you could setup a tunnel, but you won't be sending email on port 25 from a comcast residential connection.

If you want to test this hypothesis - use telnet to port 25 on your remote mail server. The connection will timeout.  Then take your laptop to a local cafe that has free wifi and do the same thing - should work. Oh - don't ever type in your password when using wifi you don't control, at least not without a VPN active first.

POP3s?  We switched to imaps around 1998 and never looked back.

---

### Post by grey1beard on 2015-09-19
That port designation - 465/tcp - I don't recognise the tcp part. 
Grateful for an explanation.
I've just tried changing my port setting to 465, but neither authenticated or otherwise works, with or without ssl encryption, so I fear I'm no further forward.

John

---

### Post by TheFu on 2015-09-20
Talk to the mail server admin. THEY have to allow ports other than 25 to be used. I've never heard of an email provider that didn't.

tcp is just a protocol layer. Wikipedia has more information.

---

### Post by grey1beard on 2015-09-21
OK I'm now completely confused by trying to set up a second account here in the USA, with a different isp, a different protocol, different username and passwords, so it's back to starting over.
I'm making the basic assumption that if I set up an account with the settings made the 'Default', and with no other account details ticked in the list of accounts, only that one makes an attempt to send/receive.
Second assumption, that if another account, with different protocol/settings is ticked, then that one will also be 'sent/received' in due order.
Third assumption, that if the two accounts, one, let's say POP and the other IMAP, then the browser will go through the process without confusing the two lots of settings.
Am I right so far ?
John

---


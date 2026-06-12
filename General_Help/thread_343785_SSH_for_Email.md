---
title: "SSH for Email"
date: 2007-01-22
forum: General Help
---

### Post by cssutto on 2007-01-22
Is there a good simple "how to" for setting up ssh tunneling for email?

CSSJR

---

### Post by kidders on 2007-01-22
Hi there,

There's nothing to it, really. To tunnel an SMTP connection to a remote box over SSH, all you need is something along the lines of **sudo ssh -L25:localhost:25 ....**

I can't help wondering why you'd want to do that though, since SMTP supports encryption in its own right anyhow.

---

### Post by cssutto on 2007-01-22
Because:

[http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html)
[http://www.stopdesign.com/log/2005/02/07/secure-email.html](http://www.stopdesign.com/log/2005/02/07/secure-email.html)

I have used a wire service for my ISP's unltil some months ago when I changed to Alltel's cell wire serv ice.  I suspect that is no more secure than the the WiFi deals in the coffee shop or hotel.

CSSJR

---

### Post by kidders on 2007-01-22
Ah I see...

If, for instance, you were using an unencrypted (or poorly encrypted) WLAN *and* you had a mail SP that offered no encryption support, your mail would be very vulnerable as it travelled between you and your AP. You could tunnel commnications over ports 25 and 143, say, through the AP over SSH ... or you could simply switch to a proper service provider. (Even Gmail supports POPS and SMTPS.)

Something like **sudo ssh -L25:mail.whoever.com:25 -L143:mail.whoever.com:143 -i ~username/.ssh/id_rsa -l username -f -N your.ap.address** would do the trick. The command's a bit long, but you could always throw it in a shell script. (The "sudo" is required to forward privileged ports.)

I hope that helps.

---

### Post by cssutto on 2007-01-22
Thanks.

That gets me closer.

I'll have to work on this later.

CSSJR

---


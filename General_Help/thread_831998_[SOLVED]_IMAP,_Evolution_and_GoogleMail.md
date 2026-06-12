---
title: "[SOLVED] IMAP, Evolution and GoogleMail"
date: 2008-06-17
forum: General Help
---

### Post by alecspoons on 2008-06-17
Can anybody help me figure out why I can't get IMAP to work with Evolution and GoogleMail, please?

I'm pretty sure I've got the right settings:

Receiving
Server type - IMAP
Server - imap.googlemail.com:993
Security - SSL
Authentication Type - password

Sending
Server type - SMTP
Server - smtp.googlemail.com:465
Security - SSL
Authentication type - plain

In 'IMAP Headers', I've selected 'Basic'.

I've got it working without any problems in Thunderbird, so the ports are open, and IMAP is enabled on GoogleMail. The username and password are OK, because if I swap to POP it works. There doesn't seem to be any folders in the left-hand pane that I might have missed.

When I click 'Send/Receive', it seems as if Evolution is checking, but no new mails are received.

Any suggestions??

Thanks

---

### Post by alecspoons on 2008-06-17
I can't believe it!

After days of trying to get this work, and just a few minutes after posting this, I've got it working.

Here's how:

I created a whole new IMAP email account in Evolution using the settings I saw at [http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml]("http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml") which are slightly different - using TLS for sending.

It works fine - occasionally takes a little longer than POP, but seems OK.

SOLVED! Hooray!

---

### Post by fermin on 2008-07-17
The instructions in the link you posted worked for me too, after having been weeks without been able to solve this problem. Thanks.:)

---

### Post by Steve H on 2009-08-16
Thanks for that, just couldn't get it working. I couldn't work out where the ports were supposed to go....at the end of the URL with a colon, so simple.

Anyway thanks again, you saved me pulling my hair out for an hour!!

:)

---

### Post by danielbu on 2009-09-22
I did all this but I don't get the popup password request...

---


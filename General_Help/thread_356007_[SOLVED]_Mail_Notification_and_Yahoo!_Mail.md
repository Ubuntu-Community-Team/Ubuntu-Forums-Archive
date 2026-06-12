---
title: "[SOLVED] Mail Notification and Yahoo! Mail"
date: 2007-02-07
forum: General Help
---

### Post by victorbrca on 2007-02-07
Hi all,

 
  Anyone ever configured Mail Notification with Yahoo POP?

  I had no problem configuring Evolution to download the e-mails, but Mail Notification has some different configurations, which I tried some combinations but could not get it right...

Thanks,


Vic.

---

### Post by victorbrca on 2007-02-08
Well, if anyone ever look for this, this is how I got it setup


- Mailbox type - POP
- Mailbox name - Your complete e-mail address
- Hostname - Yahoo POP server - eg: pop.mail.yahoo.ca
- Username - Your username 
- Password - Your password

Choose details
- Connection type - in-band SSL, port 110 (even though yahoo tells you to use 995)
- Authentication mechanism - Autodetect (I did not try one by one. The problem with this is that it will try to authenticate using all protocols in the order that is shows, so if a plain authentication method, no encryption, is before the one that yahoo uses, it means that your password will be sent unencrypted over the net and it could be retrieved by a hacker. I'll try them one by one when I have a chance and update this)


Vic.

---

### Post by wxnker on 2007-02-08
I use it everyday. It works perfect if you use the information regarding pop3 in your yahoo mail account.

---


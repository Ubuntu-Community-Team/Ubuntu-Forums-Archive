---
title: "Mail Server Authentication Setup Problem"
date: 2007-11-11
forum: General Help
---

### Post by webmasteroy on 2007-11-11
Linux Ubuntu (debian) server edition 7.10

I have been following a tutorial on this page: <link expired>
I havn't had a major problem till I got to: "3c. Configure SASL Authentication with TLS" I can't seem to get this to work properly I did everything that it asks me to do, but I get this error when I try to restart dovecot.

```

Error: Error in configuration file /etc/dovecot/dovecot.conf line 772: Auth sectionno allowed here (section changed at line 772)
Fatal: Invalid configuration in /etc/dovecot/dovecot.conf

```

Line 772 is: auth default2 {

My full dovecot.conf file can be read here: [http://www.oyoystudios.frih.net/dovecot.txt ]("http://www.oyoystudios.frih.net/dovecot.txt")

So basically what this section of the page is for is to authenticate mail when you send it externally so that spammers can't use your server or whatever. You can't send mail without this supposedly in mail clients. 

You should also no I did some things to the file when I got this error before one of which I commented out the whole auth default2 section I didn't get the error when restarting but when I tried to send mail in outlook I couldn't it just prompting me to signin as if my password was wrong but I could email from an external email to the server. This is when I had the server requires authentication on. I have tried everything it says on that page as well as search google.

One thing to not is that when I don't the server requires authentication selected I can send and recieve mail internally like using out look to send mail to the address that sent it. so like [email]test@test.com[/email] to [email]test@test.com[/email] if the domain set up was test and the user setup was test.

So basically I am just stuck on the last part of setting up the mail server. If someone could help me solve this I will be in your debt.

Thank You So Much!

---


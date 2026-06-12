---
title: "Email via postfix not delivered to gmail account"
date: 2018-10-05
forum: General Help
---

### Post by PeterTaps on 2018-10-05
Hello,

Environment: Clean Ubuntu 18.04 server

Our main DNS server and email server are at GoDaddy. Let's say my company's domain is abc.com.

I have installed and configured postfix on a new Ubuntu 18.04 server. This machine's address is mail2.abc.com.

Besides root, there is only one user account - peter.

Forward and reverse DNS entries have been set correctly. 
MX records have been set correctly.

Verified network settings as follows:

$ dig mail2.abc.com MX
$ dig abc.com MX
$ dig mail2.abc.com a

Here are the important lines from /etc/postfix/main.cf


virtual_alias_domains = abc.com
virtual_alias_maps = hash:/etc/postfix/virtual

Here is  /etc/postfix/virtual:

@mail2.abc.com peter
@abc.com peter

The first line basically says an email sent to any address at mail2.abc.com be forwarded to peter
The second line also does the same thing for any email with "to" address containing "@abc.com."

With this setup, I am able to send emails to another personal account with the following "FROM" addresses:

[email]peter@mail2.abc.com[/email]
[email]peter@abc.com[/email]

However, when I test sending emails to my gmail account, I am running into a problem. FROM address "peter@mail2.abc.com" works fine. The email is received in my gmail account. However, FROM address [email]peter@abc.com[/email] does not seem to work. Although there is no error reported in /var/log/mail.log, the email never makes it to my gmail account. 

Seems the email is not getting rejected as it does not bounce back.

I have verified that abc.com and mail2.abc.com are not blacklisted in any spam database.

I am wondering what could be going wrong.

Also, is there a way to get a detailed report from "gmail.com" on why the email has been detained. Perhaps I can send an email to "test@gmail.com" or something like that.

Appreciate your help.

Regards,
Peter

---

### Post by rainintheface on 2018-10-05
I have found in the past that if I set up my Gmail account to "send as" [email]peter@abc.com[/email], go through all the setup steps, then that now allows my email from [email]peter@abc.com[/email] to actually arrive at Gmail too. In Gmail: Settings/Accounts and Import/Send Mail As/Add Another Email Address.

---

### Post by SeijiSensei on 2018-10-06
Try this test:

```
telnet gmail-smtp-in.l.google.com 25
```

Do you get a response with a banner like this?

```
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP w64-v6si2250626qkb.193 - gsmtp

```

If not, your ISP blocks outbound SMTP connections.  They may have a server that you can use to relay outbound mail, or they may simply block it entirely.  This is a security precaution to prevent infected computers from being turned into spambots.  That was the dominant method of spamming a few years back.

"^]" means hold down the Ctrl-key and hit the right square bracket.  Type "quit" at the prompt that follows.

---

### Post by PeterTaps on 2018-10-06
Thank you for your help. This is not a problem as, from the same machine, I can successfully send email as [email]peter@mail2.abc.com[/email] to my gmail account. Just that sending mail as [email]peter@abc.com[/email] is being detained.

---

### Post by SeijiSensei on 2018-10-07
What errors do you see in /var/log/maillog?

Do you have an [SPF]("http://www.openspf.org/Introduction") record in your DNS for abc.com and mail2.abc.com?

---


---
title: "Is there a howto on running multiple email accounts in one local mail account"
date: 2006-12-03
forum: General Help
---

### Post by funk19 on 2006-12-03
Here's my situation. 
I have numerous pop3 mail accounts all receiving a ton of spam to each account. 

Here's what I would like to achieve:

1) Setup a local mail account using something like postfix
2) Use some type of a pop3 connector to automatically check and download email from my pop3 accounts
3) Before sending email to the local mail account I want all email to go through a spam filtering system like spamassassin or similar and bounce "spam " email back to sender.
4) Once email has been through spam filter (and passed) then deliver the email to my local mail account.

Why do I want to do this?

1) Eliminate spam from my accounts and the time I spend sifting through spam
2) Only have one local email account setup in Evolution rather than 15 or 20 pop3 mail accounts

Any ideas how if this can be done?

Thanks in advance!!!

---

### Post by lamego on 2006-12-03
> 1 and 2) Setup a local mail account using something like postfix
Try fetchmail, it will allow you to fetch email from several email accounts to your local linux account
> 3) Before sending email to the local mail account I want all email to go through a spam filtering system like spamassassin or similar and bounce "spam " email back to sender.
Fetchmail delivers your mail locally using your local MTA (postfix or other) so you just need to setup spamassasin or any other antispam system locallly
Sending spam back to the sender is not very wise, most of the times the sender is forged so you will just be creating even more spam
> 4) Once email has been through spam filter (and passed) then deliver the email to my local mail account.

fetchmail+anti-spam

---

### Post by funk19 on 2006-12-03
Thanks lamego

I'm going to bash this out now and see if I can get it all working.!!

---


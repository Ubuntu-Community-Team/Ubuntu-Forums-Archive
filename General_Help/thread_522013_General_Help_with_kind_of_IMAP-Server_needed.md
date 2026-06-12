---
title: "General Help with kind of IMAP-Server needed"
date: 2007-08-10
forum: General Help
---

### Post by TakeshiKovacs on 2007-08-10
Hey guys,

I´ve been looking into this topic many, many times, not with that much of a success as you may guess, so hopefully one of you could be so kind to point me to right direction.

Here is what I wanna do:

Over the years I got myself several different email addresses, all of them are pop3. For some time I was using the server of a friend to collect all my emails via fetchmail from the different provider and them in a IMAP-account he was hosting on his server. Well, the server is gone, but I still have the addresses. I already read several tutorials about setting up postfix, courier, etc. But most of them are not what I wanted. I don´t wanna become a mail provider. ;)

So, I just want to have an IMAP-account on my Ubuntuserver running at home, collecting the mails from the pop3-accounts, collecting the localmails (I have several applications that should send mails to the local user) and make them available to me via webmailer (squirrelmail) and via thunderbird when I´m at home. My IP changes every 24 hours and I just want to be able to sent mails as the pop3-users that I´m also collecting the mails from. For example, I want to collect my gmail mails to an IMAP account and be able to send mails as that gmail user.

Hopefully you guys get what I want and I bet, that there are lot´s of other people out there who wanna have something like this. Point me to the right direction and I write an HowTo in the wiki about it. I just need some help in the beginning :)

Thx in advance.

---

### Post by TakeshiKovacs on 2007-08-27
*bump*

Really no one that can give me a hint?

---

### Post by wislon on 2007-09-06
Hi Takeshi (I'm a Richard Morgan fan too :) )

I've just done a basic howto which should pretty much cover what you are trying to do:

I'm by no means an expert at this, but this pretty much works for me:

[http://ubuntuforums.org/showthread.php?t=395522](http://ubuntuforums.org/showthread.php?t=395522)

(see page 2, post #14)

Hopefully it will give you a place to start. I haven't done Gmail yet, but it works just peachy with other pop3 accounts. 

If you have a dynamic IP, try looking on this forum for 'dyndns.org' to register a free domain to track your IP address/hostname from the internet.

As for squirrelmail etc., you're on your own :)

HTH :)

---

### Post by wislon on 2007-09-06
...and there's quite a bit more here (which I've just discovered)

[http://ubuntuforums.org/showthread.php?t=425655](http://ubuntuforums.org/showthread.php?t=425655)

collecting email from gmail and using it as an outgoing relay too. gonna try this myself soon!

---

### Post by TakeshiKovacs on 2007-09-11
Thanks for your answer wislon. I somehow managed to get everything working so far, except one particular thing, which really bothers me.

In Thunderbird I can set different SMTP servers for the identities I´m using, which is exactly what I wanted, since I´m collecting my mails from different pop3 accounts. Unfortunately this doesn´t seem to be possible with squirrelmail, or I´m missing something here?

Any suggestions would be really nice.

---

### Post by wislon on 2007-09-12
Takeshi, unfortunately I have never used squirrelmail myself or set it up or anything like that, so unfortunately I can't help you with that. Are you pulling all the mails from the pop3 servers into one IMAP account, or into 3 separate IMAP accounts? 

My guess is that there must be something for setting an identity based on the login for squirrelmail if you're doing the latter. 

Another option may be to set up a local mail server (like postfix) on that same box, and use a "smarthost" to deliver the emails for you (one of your ISPs will allow you to send email using authorisation, which means you can send mail with a "From:" address of anything as long as you have the right credentials to send mail through that server). 

And then point the squirrelmail smtp at the postfix SMTP server running on that box. I have not done this myself, but there's plenty of info around if you have a poke around on these forums.

Good luck with it! :)

---

### Post by TakeshiKovacs on 2007-09-12
Well, I guess "luck" is the right word when it comes to mailserver in linux ;)

Anyway, that is a good hint and I´ll give it a try when I´m back home.

Thanks though.

---


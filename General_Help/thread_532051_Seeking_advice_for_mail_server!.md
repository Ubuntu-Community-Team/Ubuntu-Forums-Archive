---
title: "Seeking advice for mail server!"
date: 2007-08-22
forum: General Help
---

### Post by markonhismobile on 2007-08-22
I have an Ubuntu box that is left on 24/7 - I was wondering if it is possible to set it up so it checks my Yahoo account (POP3) for mail, filter any spam, do an AV check, download it and allow me to pick it up from the local computer using an e-mail client such as Thunderbird?

I have had a look around and have tried installing and configuring Procmail, Spamassassin, Postfix and Fetchmail (I didn't get as far as AV checking yet - but I would like to implement it!)

The furthest I got was getting Fetchmail to check my Yahoo account and download a new message there that it delivered to the local mailbox for my user. I didn't try then collecting this mail as I didn't have access (directly) to my PC running TB!

Any advice or suggestions of programs to use would be greatly appreciated!

---

### Post by Rescue9 on 2007-08-25
Yes... this is possible! I've got this same setup running right now. It checks a few gmail accounts and a yahoo account, downloads the messages, runs them through spam and virus check and delivers them to my local mailbox that is setup as imap. This way all mail is left server side and I can access it whenever I want and however I want; palm treo, squirrelmail, thunderbird, outlook, etc.

I followed a few howto's:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

I also got a CACert so I didn't get those annoying messages about the cert being server signed.
[http://wiki.cacert.org/wiki/courier?highlight=%28Courier%29](http://wiki.cacert.org/wiki/courier?highlight=%28Courier%29)

---

### Post by markonhismobile on 2007-09-05
thank you for the links, I've just had a look over them and the second one looks like a rather neat solution.

I just wanted to check tho, when I'm setting up the "virtual" users that mail is received for do I use my actual yahoo account in there or do I need to use something else like Fetchmail to first retrieve it to the local machine as I'm not actually having the e-mails sent directly to this server?

In the meantime I'll try and make some inroads into getting that setup implemented and try some testing!

---

### Post by markonhismobile on 2007-09-05
Just a quick update, been hacking away at my box from work all afternoon (it's been fairly quite! god bless SSH!)

I've got Fetchmail retrieving mail from my Yahoo account, Postfix delivering it to my local mailbox on the server - running it through Spamassasin/ClamAV etc first!

All i have to do now is enable the retrieval so I can pick it up from my PC's with Thunderbird and it should be good to go!

---


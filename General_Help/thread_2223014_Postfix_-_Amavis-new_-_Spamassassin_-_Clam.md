---
title: "Postfix - Amavis-new - Spamassassin - Clam"
date: 2014-05-09
forum: General Help
---

### Post by Bjarke_Emborg_Kragelund on 2014-05-09
Hello,

Have been following this guide : [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew).

Running on Ubuntu 14.04 LTS - x64.

I do not receive SPAM - and I have tested with various SPAM-mails, and they are getting caught. So I believe the setup is somewhat valid.

Below is entry from /var/log/mail.log

```
May  9 09:30:21 mail amavis[2912]: (02912-12) Blocked SPAM {RejectedOpenRelay,Quarantined}, [208.85.188.119]:52712 [80.82.79.254] <mailer@maysoft.org> -> <someone@somewhere.tld>, quarantine: T/spam-Tlyru6aJPa9U.gz, Queue-ID: 929F914056D, Message-ID: <2015476595@bom.baretconoy.com>, mail_id: Tlyru6aJPa9U, Hits: 10.564, size: 18809, 4151 ms

```

If i read the above correct, the SPAM-Score is 10.564?

Now I would like the mail to be forwarded to the enduser with a SPAM-tag in subject + the SPAM-score.

I have edited the /etc/amavis/conf.d/50-user, and added :

```
$final_spam_destiny       = D_PASS;
```

All is almost well - the mails are now stored in the inbox, but without header X-Spam-Level, and no alteration of the subject.

What could I be missing?

Brgds.
Jugger

---

### Post by Bjarke_Emborg_Kragelund on 2014-05-28
/etc/mailname is the *DOMAIN* and *NOT* the FQDN - which was my mistake!

---


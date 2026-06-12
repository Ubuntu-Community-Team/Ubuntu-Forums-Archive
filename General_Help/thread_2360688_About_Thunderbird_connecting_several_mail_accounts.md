---
title: "About Thunderbird connecting several mail accounts"
date: 2017-05-07
forum: General Help
---

### Post by satimis on 2017-05-07
Hi all,

Godaddy share hosting
Thunderbird running on a VM of VirtualBox

I have following webmail accounts:```

[email]user1@domain1.com[/email] 
[email]user2@domain1.com[/email]
[email]user3@domain1.com[/email]
[email]user1@domain2.com[/email]
[email]user2@domain2.com[/email]
[email]user3@domain2.com[/email]
[email]user1@domain3.com[/email]
[email]user2@domain3.com[/email]
[email]user3@domain3.com[/email]

```
etc.

Can I run Thunderbird connecting all of them?  

I have no idea what will be the term for googling such an information.  Please shed me some light.  Thanks in advance.

I have been googling with "thunderbird shared mailbox linux" and found following links;

Thunderbird: accessing a shared mailbox without Exchange
[https://www1.udel.edu/it/help/thunderbird-3/thunderbird-3-create-alternate-incoming-mailbox.html](https://www1.udel.edu/it/help/thunderbird-3/thunderbird-3-create-alternate-incoming-mailbox.html)

Adding shared mailbox to Thunderbird via IMAP
[http://forums.mozillazine.org/viewtopic.php?f=39&t=663143&start=0](http://forums.mozillazine.org/viewtopic.php?f=39&t=663143&start=0)

How to set up thunderbird with several IMAP accounts and using one inbox and outbox
[https://support.mozilla.org/en-US/questions/1080471](https://support.mozilla.org/en-US/questions/1080471)

Would they be related?

Regards
satimis

---

### Post by #&amp;thj^% on 2017-05-07
With Thunderbird you can set-up multiple email accounts in the same profile. The mail will be stored in separate directories in the file system anyway. Simply run the new account wizard to set-up the accounts.

[https://support.mozilla.org/en-US/kb/automatic-account-configuration](https://support.mozilla.org/en-US/kb/automatic-account-configuration)

Alternatively you can set-up multiple profile, one for each account and create desktop shortcuts for each profile. That doesn't make much sense for me though.

---

### Post by satimis on 2017-05-07
> **1fallen said:**
> With Thunderbird you can set-up multiple email accounts in the same profile. The mail will be stored in separate directories in the file system anyway. Simply run the new account wizard to set-up the accounts.

[https://support.mozilla.org/en-US/kb/automatic-account-configuration](https://support.mozilla.org/en-US/kb/automatic-account-configuration)

Alternatively you can set-up multiple profile, one for each account and create desktop shortcuts for each profile. That doesn't make much sense for me though.
Hi,

Thanks for your advice.

Performed following steps

Start Thunderbird```

-> Email
Mail Account Setup
(check) IMAP (remote folders) (I expect keeping a copy of each email on the online webmail)
Incoming: IMAP, mail.domain1, STARTTLS
Outgoing: SMTP, mail.domain1. STARTTLS
Username: aaa

```

To continue adding another mail account```

click [Get a new account] 
...... 

```

After creating all mail accounts```

click  [done]

```

Please advise before proceeding further.  Thanks

Regards
saimis

---

### Post by #&amp;thj^% on 2017-05-07
I have found for myself..that setting up one account at a time is best.
I had some faulty config's setting them up one after another.
Incoming and Outgoing ports are very important here.

---

### Post by satimis on 2017-05-07
> **1fallen said:**
> I have found for myself..that setting up one account at a time is best.
I had some faulty config's setting them up one after another.
Incoming and Outgoing ports are very important here.
Done.  Thanks

Each user has its own folder.  There is quite a long list.  Would it be possible grouping users in their own domain account?

satimis

---

### Post by #&amp;thj^% on 2017-05-07
> **satimis said:**
> Done.  Thanks

satimis

Very Glad you got it working, :)
> **satimis said:**
> D  Would it be possible grouping users in their own domain account?

satimis
Albeit I've never done this or have not needed to....but I will test first myself and report back here in this thread.
It does sound do-able but I need to set it up myself to advise anything relevant,
Talk soon,,,Regards

---


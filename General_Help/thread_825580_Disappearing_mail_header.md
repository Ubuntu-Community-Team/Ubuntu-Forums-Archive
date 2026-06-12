---
title: "Disappearing mail header"
date: 2008-06-11
forum: General Help
---

### Post by VSpike on 2008-06-11
I have a setup where I use fetchmail to get mail from 2 POP3 accounts.  I deliver locally to postfix and then use maildrop to filter and deliver to a Maildir on my account.  I then use dovecot IMAP to access all my mail from anywhere.

This works well, but something has changed.  Because I retrieve two mail accounts, I use maildrop to filter into different incoming folders.  Up till now, both accounts have delievered mail with an "Envelope-to:" header which allows me to identify the account, even on BCC mail where otherwise my address does not appear.

However, on one account the "Envelope-to:" header has suddenly vanished.  I have not changed anything locally.  It is still present on mail from the other account.

Can anyone tell me why this might happen? I'm not even sure where that header gets added, or why it might be stripped.  In fact, if anyone has a link to a good detailed explanation of the various headers that would be handy too.

Also, if anyone has another suggestion as to a good way to filter by incoming account that would be handy.

Thanks!

---

### Post by HalPomeranz on 2008-06-11
Headers like Envelope-To are added purely at the discretion of the email server you're pulling your email from with fetchmail.  It sounds like your upstream mail server changed their configuration and stopped adding this header.

I was looking at the fetchmail manual page, and it appears you might be able to fake things out by using the "-E" option to tell fetchmail to look for the envelope recipient in a different header:

[http://fetchmail.berlios.de/fetchmail-man.html#10](http://fetchmail.berlios.de/fetchmail-man.html#10)

But make sure you read and understand the discussion in these later sections:

[http://fetchmail.berlios.de/fetchmail-man.html#41](http://fetchmail.berlios.de/fetchmail-man.html#41)
[http://fetchmail.berlios.de/fetchmail-man.html#34](http://fetchmail.berlios.de/fetchmail-man.html#34)

I personally don't use fetchmail, so that's the limit of my helpfulness on this one.  Good luck!

---

### Post by VSpike on 2008-06-12
Thanks Hal.  I think I agree with the first part of your analysis.  However, I think you misunderstand slightly - I'm not using fetchmail for multidrop, so it is not using the envelope headers at all.  

Fetchmail delivers multiple email accounts to one local account associated with my real unix user account.  I then use maildrop as the delivery agent to filter mail to local folders based (in part at least) on which account they came in on.  That is the point at which I was using the envelope header - purely for maildrop.

---

### Post by HalPomeranz on 2008-06-12
> **VSpike said:**
> Thanks Hal.  I think I agree with the first part of your analysis.  However, I think you misunderstand slightly - I'm not using fetchmail for multidrop, so it is not using the envelope headers at all.  

Fetchmail delivers multiple email accounts to one local account associated with my real unix user account.  I then use maildrop as the delivery agent to filter mail to local folders based (in part at least) on which account they came in on.  That is the point at which I was using the envelope header - purely for maildrop.

My mistake, sorry.  Nevertheless, some of the same points still apply-- there may be other mail headers maildrop could use to sort the incoming mail into folders, but those other headers may not be reliable in all cases.

---

### Post by VSpike on 2008-06-13
Exactly... BCC'd messages for example don't contain my address anywhere!  The benefit of the Envelope-to -- up until now at least -- was precisely that it was reliable.

I suppose since the other account still includes one, I could swap the logic and work on the lack of one.

However, it may be a good time to do something that I've been meaning to do for a while which is to create two virtual mail accounts - one for work mail and one for home mail - and use fetchmail to route each pop3 account into its own virtual user's mail account locally.  That would be neater in terms of organisation rather than mashing them into a single account and then filtering into folders.  It also avoids the original problem.

---


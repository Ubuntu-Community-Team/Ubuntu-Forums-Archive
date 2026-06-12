---
title: "Evolution and checking pop email"
date: 2008-02-12
forum: General Help
---

### Post by varaonaid on 2008-02-12
Hi,

I've been using Evolution for several months now and have never run across this current issue.  My POP email is showing that it's check the accounts successfully but when I didn't receive any email this morning, I got suspicious. I checked those account online vial webmail and, sure enough there's mail on the servers that hasn't been downloaded by Evolution - even though it's showing that it's current.  I tried everything I could think of - restarting Evo, restarting Ubuntu, unchecking the saved passwords, deleting the account and entering it all over again.  Nothing works.  Even when I unchecked the "save password" option and restarted, it never asked me for the password.  When I deleted the account and entered it fresh (checking the "save password" option), it never asked me for the password.  This leads me to believe that it isn't really communicating with the POP server at all or it would get some sort of an error message, correct?

This was a sudden change as last night, it seemed to be checking email just fine.  Checking via webmail confirms that the emails that were sent to me last night came through.  Also, it seems that I can send email via the same accounts that are affected without problem (I confirmed that the email I sent went through and was received).

So, I'm perplexed as to what to do to fix this.  It seems that somewhere, the POP email receiving functions are corrupted for a couple of my accounts (a few of my accounts are affected, others are not).  Can anyone help me troubleshoot this or offer any suggestions as to what to do to resolve the situation?  Unfortunately, at the moment, it makes Evolution completely unusable and useless.  

I'd appreciate any thoughts or suggestions.  Thanks so much in advance!

Running Ubuntu Gutsy (7.10)/Evolution 2.12.1

UPDATE: I found where Evolution stores my passwords and deleted the file which forced it to create a new one when I reopened it.  This didn't solve the problem.  In fact, I think that the problem is getting worse.  My gmail account which was working fine, now checks email, says that it downloads it and it never shows up in my inbox.  I confirmed that a new message came in by check the account via webmail.  So, it thinks it's checking the mail, and indeed could be but is somehow losing the messages when they arrive.  Any ideas?

---

### Post by varaonaid on 2008-02-12
In digging through some of the "cache" folders in /.evolution, I found that there are in fact emails that were received and downloaded today but never showed up in my inbox.  So they have been delivered to my computer but aren't showing up.  This is awful. :(

Please let me know if you have any thoughts or advice as to how to fix.  Thanks!

---

### Post by solitaire on 2008-02-12
The same happened to me on one of my accounts.

I didn't have the time to problem solve it, so i just installed Thunderbird insted and transfered my mails over.

---


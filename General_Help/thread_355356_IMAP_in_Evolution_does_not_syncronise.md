---
title: "IMAP in Evolution does not syncronise"
date: 2007-02-07
forum: General Help
---

### Post by cez801 on 2007-02-07
I'm running Evolution with an IMAP account over SSL. But for some reason Evolution does not seem to be syncing my changes back to the IMAP account.

1. Marking an email as read in evolution, does not seem to mark it as read in my IMAP server.
2. Deleting emails from evolution does not delete it from my IMAP server.

I noticed this because I use mail-notification, which shows there are unread emails in my account. If I login to the webmail server for the IMAP account I can mark it as read - and mail-notification changes status.

I also found that if I move a mail in evolution to a different folder and then do a send/receive, then evolution updates the IMAP server correctly.


I'm pretty sure it is not a problem with my IMAP server, as it did work with Thunderbird on Windows (I have not tried thunderbird on Unbuntu yet - thought I'd give Evolution a spin first).

---

### Post by dcstar on 2007-02-07
> **cez801 said:**
> I'm running Evolution with an IMAP account over SSL. But for some reason Evolution does not seem to be syncing my changes back to the IMAP account.
........
I'm pretty sure it is not a problem with my IMAP server, as it did work with Thunderbird on Windows (I have not tried thunderbird on Unbuntu yet - thought I'd give Evolution a spin first).

I believe that there is a Sync option in the Preferences for the account you have set up.

---

### Post by cez801 on 2007-02-08
> **dcstar said:**
> I believe that there is a Sync option in the Preferences for the account you have set up.

Yes. There is in Preferences, Edit Account, Receiving Options Tab - it is called Automatically Synchronize Remote Mail Locally.

I do already have that option checked on when I experienced these problems.

---

### Post by jfxberns on 2008-04-05
I am experiencing this problem as well.  So far, I have not seen an answer here on the forums. 

The problem is not the mail server (I am using GMail and syncing op items works properly when using Thunderbird).

Any ideas out there?

---

### Post by jfxberns on 2008-04-05
Oh--and I have tried changing Email Accounts --> Receiving Options --> Automatically synchronize remote mail locally.   No change.

To reiterate the problem:

If I move a mail to a different folder or mark a mail as read, the change made locally is not reflected on the server.  If i do the same think in Thunderbird, the change IS reflected on the server.

---


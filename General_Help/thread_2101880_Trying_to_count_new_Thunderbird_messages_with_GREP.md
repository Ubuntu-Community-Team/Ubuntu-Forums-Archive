---
title: "Trying to count new Thunderbird messages with GREP"
date: 2013-01-05
forum: General Help
---

### Post by Petro Dawg on 2013-01-05
I'm trying count the number of new messages in a specific IMAP email account setup in Thunderbird using the following grep command

```
grep -c "X-Mozilla-Status: 0000" ~/.thunderbird/a7syjn0d.default/ImapMail/imap.gmail.com/INBOX
```As far as I can tell the path is correct; this is the path shown under "local directory:" in Account/Server settings for this account.  

I have three unread messages in this account, but "0" is always returned.  I can get my other two POP3 accounts to display unread messages correctly using a similar grep command with out a problem.

It appears to me as if Thunderbird is not assigning unread messages in that IMAP account with the 0000 status.  Is that possible?  Or am I just in the wrong directory?

I've also tried "All Mail" in another directory...

```
grep -c "X-Mozilla-Status: 0000" ~/.thunderbird/a7syjn0d.default/ImapMail/imap.gmail.com/[Gmail].sbd/All\ Mail
```with the same results.

Let me know if you have any ideas on why this isn't working.

---

### Post by Petro Dawg on 2013-01-05
I just received a brand new email and without opening it, I checked the last entry in the INBOX text file and it seems my unread email is not being assigned the 0000 status value.

This is the status of the unseen email.
```
From - Sat Jan  5 14:58:21 2013
X-Mozilla-Status: 0001
X-Mozilla-Status2: 00000000
``` 

Not sure why it works correctly for my POP3 accounts and not this IMAP.  I sure hope there is a Thunderbird guru out there that can explain this.

---


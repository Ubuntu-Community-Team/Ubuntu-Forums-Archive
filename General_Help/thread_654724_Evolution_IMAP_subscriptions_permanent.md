---
title: "Evolution IMAP subscriptions permanent?"
date: 2007-12-31
forum: General Help
---

### Post by sicofante on 2007-12-31
I'm using Evolution to check my Gmail via IMAP. I want to subscribe to just the "Inbox" and "All" folders, so I go to Folder->Subscriptions, select the folders I want to subscribe to and everything seems fine. I exit Evolution, start it again and my selections are gone; I'm again subscribed to every folder in my Gmail account.

Is there a way to make the selection of subscribed folders permanent?

---

### Post by dcstar on 2007-12-31
> **sicofante said:**
> I'm using Evolution to check my Gmail via IMAP. I want to subscribe to just the "Inbox" and "All" folders, so I go to Folder->Subscriptions, select the folders I want to subscribe to and everything seems fine. I exit Evolution, start it again and my selections are gone; I'm again subscribed to every folder in my Gmail account.

Is there a way to make the selection of subscribed folders permanent?

There may be something corrupted in your configuration.

Rename your (hidden) .evolution directory and restart Evolution, it will then create a fresh environment that you will now have to set up with your e-mail accounts.

If things now work correctly, you can then copy data from the old directory into the new one to recover your e-mails, contacts etc.

---

### Post by sicofante on 2008-01-01
1. Renaming .evolution hasn't deleted my email accounts settings. It has only deleted my virtual folders and synced emails. Where's Evolution storing my accounts info?

2. I have checked a number of times for consistency and the subscription selections are not ignored after the first restart of Evolution, but the second restart, which sounds even weirder to  me.

EDIT: Just in case it helps finding the problem: I'm using a Gmail account. Also, I've tried Thunderbird and it's not retrieving all the messages in my inbox for some reason.

---

### Post by dcstar on 2008-01-01
> **sicofante said:**
> 1. Renaming .evolution hasn't deleted my email accounts settings. It has only deleted my virtual folders and synced emails. Where's Evolution storing my accounts info?
...........

I'm not 100% sure, but it must be in your user tree somewhere.

You may want to try creating another user account, and then using the fresh home tree for your current account.

---

### Post by sicofante on 2008-01-15
I just wanted to let everybody now that there seems to be a limitation in Gmail's IMAP protocol and unsubscribing single folders is not possible. So Evolution or Thunderbird are not to blame. You can't unsubscribe any Gmail folders in any email client.

It's nice to know it's not the email client's fault.

---


---
title: "evolution errors &quot;mismatch after sync&quot;"
date: 2007-12-08
forum: General Help
---

### Post by calldrin on 2007-12-08
Yesterday I started to get errors using Evolution.

" Error while fetching mail
Summary folder mismatch even after a sync"

This error pops up under many operations. 
Deleting trash, as well as every time I send and receive mail.etc.
 Someone suggested I delete the mbox.ev_summary file.
I have no idea where is is located and I don't know how to find it..
Please ... easy step by step help if you can ;-)

Chuck

PS: I'm in a real "bind" as I have several hundred emails that I must use!!

---

### Post by pjalegria on 2007-12-08
I wont to now it too...

---

### Post by danmiddle2 on 2008-06-12
> **calldrin said:**
> Yesterday I started to get errors using Evolution.

" Error while fetching mail
Summary folder mismatch even after a sync"

This error pops up under many operations. 
Deleting trash, as well as every time I send and receive mail.etc.
 Someone suggested I delete the mbox.ev_summary file.
I have no idea where is is located and I don't know how to find it..
Please ... easy step by step help if you can ;-)

Chuck

PS: I'm in a real "bind" as I have several hundred emails that I must use!!

You need to delete the corresponding .ev-summary file to the folder you are having difficulty with. They are only indexing files and are re-created.
i.e.
~/.evolution/mail/local/Inbox.ev-summary
or
~/.evolution/mail/local/Outbox.ev-summary
or
~/.evolution/mail/local/Sent.ev-summary

etc.

Before you do this, load evolution, switch to "offline mode" and then under preferences untick all your accounts. Then close evolution... delete the files (I just delete all of them when it happens). restart evo... and it will re-create the files. this may take a few mins.

Then re-enable your accounts. Should work. Its a known bug.

Hope that helps

Dan

---


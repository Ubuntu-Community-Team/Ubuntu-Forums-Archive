---
title: "Alpine: Showing folders, no messages"
date: 2007-12-04
forum: General Help
---

### Post by daenney on 2007-12-04
Hey guys,

Just started using Alpine and because I have multiple mail accounts I decided to use Alpine's folder collections.
So i configured a folder collection and set up the information to get it from my IMAP server.
Now this works like a charm, it neatly shows the other folders such as Drafts Sent Spam and Trash but for some reason it doesn't show the Messages themselves that should be in INBOX in the first place.
the folder collection looks like this:

```
Prive {imap.mailserver.tld/user=user@mailserver.tld/imap}INBOX.[]
```

When viewing the foldercollection I get the following:

```

ALPINE 0.99   FOLDER LIST                       Folder: INBOX                        No Messages  

                 Folders on imap.mailserver.tld/user=user@mailserver.tld/imap in INBOX.
----------------------------------------------------------------------------------------------------

Drafts[.] Sent[.]   Spam[.]   Trash[.]  

```

The problem is the No Messages as there should be a ton of messages in there...
Anyone got a clue what is going on here?

---


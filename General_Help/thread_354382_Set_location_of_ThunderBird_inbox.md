---
title: "Set location of ThunderBird inbox?"
date: 2007-02-05
forum: General Help
---

### Post by Paradoxdruid on 2007-02-05
I want to back up my gmail inbox to a local copy, just in case.  I've done this before (a while ago) with Thunderbird, and setting up my account is no problem.

But the problem is that Thunderbird downloads messages to ~/.mozilla-thunderbird/profile-and-other-sub-directories.

My home partition doesn't have enough space free for me to feel comfortable downloading my 1.4 GB of messages to it.  That's what I have storage partitions for.  But I don't know how to tell Thunderbird to change where it stores downloaded messages.

How can I set the inbox location to another file destination (I want it on /media/database/storage/gmail )?  I tried changing "local folder" and such, and all it gave me was errors about files not found when I tried to actually look at the messages it was downloading.

Thanks for any help or for steering me in the right direction!

--
Paradoxdruid

---

### Post by spin2cool on 2007-02-05
The easiest way is top copy your profile to another partition, and then softlink it.

my profile is currently at:  ~/.mozilla-thunderbird/ysbhiaq5.default

so I'll mv it elsewhere:
```
mv ~/.mozilla-thunderbird/ysbhiaq5.default /media/data/mail/
```

then link the old location to the new one:
```
ln -s /media/data/mail/ysbhiaq5.default ~/.mozilla-thunderbird/ysbhiaq5.default
```

This is the same principle used when dual-booting OSes with a shared data partition.

---

### Post by Paradoxdruid on 2007-02-06
Wow....  I really should have thought of that myself, was just flustered in the heat of the moment trying to use the Thunderbird GUI.

Thanks!

---


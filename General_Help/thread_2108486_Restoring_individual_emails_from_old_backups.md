---
title: "Restoring individual emails from old backups ?"
date: 2013-01-24
forum: General Help
---

### Post by grey1beard on 2013-01-24
Is this possible ?

I've just backed up my evolution programme, then restored from an earlier backup in my search for missing 'sent' emails.

Having several that I wish to keep, is it possible to restore only them, after I have restored my current back up, and if so, how ?

I can only think of roundabout ways, like sending them to myself, then quickly restoring my evolution before I receive them ;)

John

---

### Post by ajgreeny on 2013-01-24
If you copy the old folder ~/.evolution/mail/local/sent to the new ~/.evolution/mail/local/ but name it OLDsent you will see a folder in evolution itself called OLDsent from which you can copy those emails you wish to keep to the new sent mail folder.

Once you are happy, you can delete the OLDsent folder, ie your backups now copied to evolution, and you will have the old mails you wanted in your new evolution.

---

### Post by grey1beard on 2013-01-24
> **ajgreeny said:**
> If you copy the old folder ~/.evolution/mail/local/sent to the new ~/.evolution/mail/local/ but name it OLDsent you will see a folder in evolution itself called OLDsent from which you can copy those emails you wish to keep to the new sent mail folder.

Once you are happy, you can delete the OLDsent folder, ie your backups now copied to evolution, and you will have the old mails you wanted in your new evolution.

Thanks ajgreeny.
First problem that I can see is that I can't even find *.evolution* in my Home folder !
I've got the hidden folders visible, but no sign of the evolution folder.
Sorry to be such a pain, but where else should I be looking ?
( Must be losing it, at long last :(  )

Regards
John

EDIT Found it, a bit deeper in the file system - .local/share .... etc

---

### Post by grey1beard on 2013-01-24
There are 5 other 'sent' files - Sent.cmeta - Sent.ev-summary - Sent.ev-summary-meta -Sent.ibex.index -Sent.ibex.index.data.
Do I also need to copy any or all of those files over ?

Thanks
John

---

### Post by ajgreeny on 2013-01-24
No, just the old sent file.  The others will be made when you next open evolution.

---

### Post by grey1beard on 2013-01-25
Many thanks.
Take care,
John

---


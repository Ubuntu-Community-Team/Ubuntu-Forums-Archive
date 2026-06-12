---
title: "How to copy user settings from one laptop to another?"
date: 2008-04-13
forum: General Help
---

### Post by Muflon on 2008-04-13
Hi

I have purchased a new laptop to replace my existing model.  I wish to copy all my user settings from my existing laptop Ubuntu installation to my new laptop, specifically:

Firefox - bookmarks, cookies
Thunderbird - accounts, emails, address book
Desktop - panels, icons etc
Documents - all my home/ documents

Is there an easy way to do this or do I need to do each part manually.  Any particular advice for Thunderbird would be welcome.

Thanks

Muflon

---

### Post by Rinzwind on 2008-04-13
ALL settings are stored in the home directory.
Type 
ls -la |more
and you'll see directories and files staring with a dot.
.mozilla
contains anything relating to your browser
Just do a 
```
tar xvfz backup.tar.gz *
```
and copy that file over to your new system.

---

### Post by Tom--d on 2008-04-13
I would just copy your /home/ and put it in your new installation.

---

### Post by Muflon on 2008-04-13
Thanks for the help!

I will copy the home folder as suggested.  It sounds a lot easier than the equivalent operation in Windows. :)

Muflon

---


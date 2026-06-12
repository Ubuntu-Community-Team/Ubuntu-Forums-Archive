---
title: "[SOLVED] Thunderbird problems"
date: 2008-05-14
forum: General Help
---

### Post by cygnis1 on 2008-05-14
I am using Hardy and I am having issues with Thunderbird.  I installed the Lightning plugin and did not like it.  It takes up too much real estate.  I much prefer the older, cleaner version.  Anyway yesterday I was trying to forward an email and thunderbird locked up.  There was a compose window, but I was not able to add contacts.  It kept looking like it was working, but nothing was happening.  I finally had to force quit thunderbird.  I have unistalled Lightening and it still does it.  Has anyone else have this problem?  I am still able to recieve email, but not send. This includes new email, not just forwards. 
Thanks,
Cygnis1

---

### Post by pointone on 2008-05-14
Try:

```
apt-get install thunderbird --reinstall
```

---

### Post by cygnis1 on 2008-05-14
Thanks, but it did not help.

---

### Post by pointone on 2008-05-14
If you're not using POP, close all running Thunderbird instances and try the following:

```
mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird.bak
```

You'll have to reconfigure everything, but this will give you a clean slate.

---

### Post by cygnis1 on 2008-05-14
I am using POP

---

### Post by cygnis1 on 2008-05-14
I am not sure how I did it, but I unmarked my signature and now thunderbird works.  I think it was trying to find the signature file and couldn't.  Also my calendar is back the way I want it.
Thanks for the help.

---


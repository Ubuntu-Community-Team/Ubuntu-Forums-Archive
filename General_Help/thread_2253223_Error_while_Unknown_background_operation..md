---
title: "Error while Unknown background operation."
date: 2014-11-18
forum: General Help
---

### Post by cigtoxdoc on 2014-11-18
I do not have spam assain or other spam blockers on my system.  Why do I then get "Error while Unknown background operation.  Failed to spawn SpamAssassin (/usr/bin/sa-learn --spam --no-sync --local): Failed to execute child process "/usr/bin/sa-learn" (No such file or directory)?"

John

---

### Post by matt_symes on 2014-11-18
Hi

> **cigtoxdoc said:**
> I do not have spam assain or other spam blockers on my system.  Why do I then get "Error while Unknown background operation.  Failed to spawn SpamAssassin (/usr/bin/sa-learn --spam --no-sync --local): Failed to execute child process "/usr/bin/sa-learn" (No such file or directory)?"

John

You have something installed that is trying to spawn it for some reason.

When do you se this message ? At startup, login, randomly ?

What is the output of this command ?

```
apt-cache rdepends spamassassin
```

**EDIT**: There was a typo in the above command. I have now fixed this.

Kind regards

---

### Post by cigtoxdoc on 2014-11-18
Here is the output you requested:

johnl@john-Vostro-3500:~$ apt-cache rdepends spamassassin
spamassassin
Reverse Depends:
 |kmail
 |evolution
  spamc:i386
  yample
  wl-beta
  wl
  spampd
  spamassassin-rules-ja
  spamassassin-heatu
  spamass-milter
  sa-learn-cyrus
  sa-exim
  qpsmtpd
  p3scan
  mew-beta
  mew
  libmail-box-perl
 |kmail
  gotmail
  fuzzyocr
 |fetchyahoo
  claws-mail-spamassassin
  amavisd-new-postfix
  spamc
  spamc
  sa-compile
  sa-compile
  sa-compile
  mailman
 |evolution
  amavisd-new
johnl@john-Vostro-3500:~$ 

This happened once this morning.

John

---

### Post by matt_symes on 2014-11-18
Hi

I've been thinking about this, and although it could be one of the programs listed, there is absolutely no guarantee it is the case.

i'm wondering if we should try to tackle this a different way.

when did it start happening ? If you can give a date or a range between we can check to see what was installed or updated. That may give some clue.

Also are you getting a popup window with the error message or is it a notification ? How a are you being told about the problem ?

Kind regards

---

### Post by cigtoxdoc on 2014-11-20
This was first time I had received the above error.

John

---


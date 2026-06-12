---
title: "Spamassassin baysian database files"
date: 2008-05-02
forum: General Help
---

### Post by posterberg on 2008-05-02
Hi,

I've been running spamassassin for about four years on a quite old Slackware install. I just recently upgrade to run my mail server on a Hardy install.

Everything is working just fine except of that I can't seem to get the baysian learning database working.

This is what my /etc/spamassassin/local.cf says:
```
local.cf:use_bayes 1
local.cf:bayes_auto_learn 1
local.cf:bayes_ignore_header X-Bogosity
local.cf:bayes_ignore_header X-Spam-Flag
local.cf:bayes_ignore_header X-Spam-Status

```I also have a cron job that takes input from the special folders spam and ham from each mail user on the system. This cron job is run on a daily basis and invoke sa-learn.

sa-learn seem to be running perfectly well, it says add xxx mail to the database.

But... I never get anything indicating that it actually is using the database when checking the incoming mails. "Baysian" does never show up in the filter report...

I also can't seem to find the actual database files on the filesystem, so I am starting to wonder if the files actually do exist at all. These files where located under /tmp on my previous Slackware install.

Can anyone please help on where they are supposed to be located on an Ubuntu system, and also what their names should be.

Do I have to create the files manually before they actually are used or could this just be a simple permissions problem where Spamassassin tries to create them in a folder that it doesn't have write access to...

I am clueless and hope to get some help to get started... =)

---


---
title: "Beagle index maildir++"
date: 2007-05-13
forum: General Help
---

### Post by VSpike on 2007-05-13
Hi-

Running Ubuntu 7.04, I'm trying to test out Beagle, but for me it's majorly limited because it won't index my mail.   I use postfix + maildrop + dovecot locally to access mail via IMAP4 from my mail client which is usually Evolution.  I realise I can make Evolution store mail offline (i.e. create another copy of all the mail on the disk) to allow Beagle to index it, but I'm reluctant to do that as it seems very inefficient.

Ideally I want Beagle to index my maildir directly, which is in ~/Maildir.  It isn't, and I think the reason is that all the mail is in a large number of folders, and the folders are represented in the maildir as directories starting with a ".", e..g ".inbox.personal/"

I think Beagle is ignoring them because of the ".".  I don't want to add the all manually to Beagle, as this would be time consuming and would create a maintenance headache.

Is there any good way to get this working?

Thanks!

---


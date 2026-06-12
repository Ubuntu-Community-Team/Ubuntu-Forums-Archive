---
title: "Ubuntu 6.06.1 LTS server having trouble with courier-imap, sendmail, squirrelmail"
date: 2006-11-13
forum: General Help
---

### Post by wsl3 on 2006-11-13
I have just setup a box with Ubuntu 6.06.1 LTS, courier-imap sendmail and squirrelmail. For some odd reason, it won't create the default set of mail folders when I create a new user (or for old ones), and when you log in as a user and tell it to make the folders (in Squirrelmail), it claims not to have write access. Mutt doesn't have any luck either. 

All the folders should be stored in the users maildir (~/Maildir) and if it's using the users credentials, I don't understand why it can't create things. This happens as well when you ask Squirrelmail to create a folder, or when you launch mutt. I'm sure it's a permissions issue, I just have no idea where to fix it, and the logs have been less than helpful.
Anyone else run into this, or know where I need to adjust perms, and what I need to adjust them to?

---

### Post by wmatlock on 2007-01-18
Use the maildirmake command to create the Maildir directory in /etc/skel.

sudo maildirmake frodo/Maildir

You can also do this for each user.

Rick

---


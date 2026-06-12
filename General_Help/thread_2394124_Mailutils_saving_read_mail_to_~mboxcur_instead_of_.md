---
title: "Mailutils saving read mail to ~/mbox/cur instead of ~/Maildir/cur"
date: 2018-06-12
forum: General Help
---

### Post by thelatinist2 on 2018-06-12
I've got a mail stack using postfix and dovecot, both of which are configured to use the mailbox ~/Maildir.  I've configured mailutils to use the same mailbox, and it reads mail fine, but it's still saving read mail in mbox format to /home/${user}/mbox. My mailutils configuration is as follows:

/etc/mailutils.conf:[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]mailbox {[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  mailbox-pattern "maildir:///home/${user}/Maildir";[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  mailbox-type maildir;[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]};
[/FONT][/COLOR]

I've also set the $MAIL env variable.

~/.profile[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]MAIL=$HOME/Maildir[/FONT][/COLOR]

Any help would be appreciated.

In case it matters, I'm running 18.04 server with the latest versions of postfix, dovecot and mailutils from the default repositories.

---

### Post by thelatinist2 on 2018-06-14
Update: I was mistaken -- it's actually not saving in mbox format.  It's saving in the directory ~/mbox/cur (it has created a whole new maildir folder structure at ~/mbox, complete with new, cur, and tmp subfolders).  I suppose one workaround would be to change the mailbox in dovecot and postfix to ~/mbox, but I'd rather understand why it's not working in the first place.  I've grep'ed the whole system for "/mbox" and found nothing that should be doing this.

---


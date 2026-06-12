---
title: "Configuring squirrelmail with Maildir"
date: 2007-03-29
forum: General Help
---

### Post by vickistan on 2007-03-29
I recently installed Ubuntu Dapper Drake AMD64 version. In the transition, I switched from mbox format to Maildir. I now need to get squirrelmail to know where its mail is located. I can get to mail with mutt so I know the Maildir is where my mail is going. How do I tell squirrelmail to show the Maildir? I am using courier-imap btw.

Vickistan

---

### Post by vickistan on 2007-03-29
OK, well I can now get squirrelmail to see the right INBOX folder (the number of new messages displayed matches that I see in mutt), but when I click on INBOX, nothing appears in the right pane. The url shown when I mouseover the INBOX link is [http://www.mydomain.org/squirrelmail/src/right_main.php?PG_SHOWALL=0&sort=0&startMessage=1&mailbox=INBOX](http://www.mydomain.org/squirrelmail/src/right_main.php?PG_SHOWALL=0&sort=0&startMessage=1&mailbox=INBOX)

Is this correct? Should I not get to see the messages in my inbox when I click the INBOX link? I am new to Maildir, so perhaps I am just not understanding what I should see....

Any help would be appreciated.

Vickistan

---

### Post by vickistan on 2007-04-03
Ok. I think I know what was going on, so let me include my conclusions for the sake of others. I had used the mb2md command to transition my old mailbox to my new Maildir. My inbox (mbox) size was huge, and I think I exceeded the size that was allowed for Maildir/cur - although I have not found documentation as to what that size is. I removed all my files from Maildir/cur and it worked again. I got new mail and was able to read it in the right panel. I still have mail that I want to copy over to my new Maildir, and, yes, I keep too much mail in my inbox. Issues to be resolved later.

Vicki

---


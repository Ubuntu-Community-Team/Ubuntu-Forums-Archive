---
title: "Gmail problem. Change UserID from &quot;server&quot;?"
date: 2013-03-27
forum: General Help
---

### Post by stepheny on 2013-03-27
I have a machine running 12.04 which I use as a mail/print/apache/ftp/general server.

When I set the machine up a few years ago I called the main user "server". Probably a bad idea!

I recently set up the Postfix/Dovecote mail server to forward email fetched from my ISP provider email account to my Gmail account. Everything seems to work fine except that if I send myself an email from Gmail to my ISP provider email account the email vanishes into the ether. Postfix logs show that the email has been forwarded ok, exactly the same as an email from my ISP provider email account, but the email doesn't show up in Gmail in either the inbox or in "All Mail".

I decided to try using mailx to see if I got the same problem. Using mailx the email appears in the Gmail "All Mail" folder but not in the Inbox. I have all filters deactivated in Gmail. I noticed that the mailx email is from "server" and so suspect that maybe Gmail doesn't like this name as a sender. 

Therefore to further investigate my problem I wondered if it might be possible to change the Username to something else. Obviously changing just the username in not enough as in the terminal I am still server@mybox so I would have to change the UserID as well. Is this possible without upsetting my whole setup?

If anyone has any other ideas about what the problem with Gmail might be I would be very grateful.

---


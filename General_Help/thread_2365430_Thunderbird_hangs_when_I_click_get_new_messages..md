---
title: "Thunderbird hangs when I click get new messages."
date: 2017-07-06
forum: General Help
---

### Post by l6griffin on 2017-07-06
I have been running Ubuntu/Thunderbird for about 5 years pretty much  without problem to download my yahoo mail. Late last week I got an error  msg (this is a yahoo problem) saying that the server was not setup  leave mail on and I would have reconfigure thunderbird to delete  messages from the server. Esentially what the error was saying is I had to switch from PO to IMAP. There is no mention of tha in their ads that brag 1 Tb of email space. Not knowing better and thinking moving local  mail to folders would take them of the server. It even appeared to work. I've  been able to download mail till this morning, and error msg reappeared. I  reconfigured thunderbird to delete mail from server. I told thunderbird  to get new messages and it started to download 18k+ messages and exited  thunderbird as quick as I could. Now that computer won't download mail  when I click get new messages, it says no msg.s. That's what got me  here. 


I've deleted *.msf files. Copied all emails to a folder, deleted inbox,  deleted *.dat file, copied emails from folder to new inbox. No help  still get the same error, it either hangs or I get a msg that the folder  is in use by another operation. It looks like I'm going to have to un-install thunderbird and reinstall. is their another solution?

Will removing thunerbird wipe out my mail files?  I seem to remember it won't.

Larry

---

### Post by SeijiSensei on 2017-07-06
Reinstalling Thunderbird won't affect your settings and stored messages, but I'd back up the contents of /home/yourusername/.thunderbird where all those things are stored.

I'd close Thunderbird, rename .thunderbird to .thunderbird.bak, then start Thunderbird and recreate your account from scratch.  I don't think the problem is with Thunderbird but with synchronization between you and the server.  Create the new account with IMAP and see what happens.

---

### Post by l6griffin on 2017-07-07
Thanks for the quick reply. I'm a firm believer in the old saying 'if it ain't broke don't fix it'.I think the problem is yahoo server configuration` I uninstalled and reinstalled, renamed directories. When I brought thunderbird back up it was configured for IMAP. I tried to manually configure for POP3 and it wouldn't talk to the yahoo server. I've been thinking about ditching yahoo because of continuing irritating nuances now it's going to happen.

---


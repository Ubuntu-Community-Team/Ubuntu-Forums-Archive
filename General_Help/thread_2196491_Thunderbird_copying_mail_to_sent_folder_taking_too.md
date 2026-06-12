---
title: "Thunderbird copying mail to sent folder taking too long"
date: 2013-12-29
forum: General Help
---

### Post by michael-piziak on 2013-12-29
If I send an attachment, like 2.2 megs in size, after it's sent Thunderbird copies the mail to the sent folder and it seems to take forever to do it.   Sometimees it fails and asks if I want to try again to copy mssg to sent folder.
I'm running a core 2 duo processor, 2.8 ghz

Anyone else noticed this?

---

### Post by SeijiSensei on 2013-12-29
Where is the Sent folder?  On the local machine or on an IMAP server along with your inbox?  The latter can be slow since it requires that the message be copied over the network rather than to a local drive.

---

### Post by michael-piziak on 2013-12-29
Sent folder is on "Michael Piziak"
Other option is to switch "Michael Piziak" to local folder.
But I think my name is just what my account setting is in Thunderbird

I just switched it to "local folder"
Goes quickley; however, where did the copy of the email go?  If I click "sent" it's not in there.

Also, I just logged into my email account on the web, clicked sent, and it didn't save the emails or attachments there.

---

### Post by SeijiSensei on 2013-12-29
If you right click on the account name in TBird and choose Settings, then choose Server Settings, what kind of mail server does it say you are using?  In my case it reads "IMAP Mail Server" then gives the server's hostname.  If you are using an IMAP server, all your folders reside on the server, though TBird will maintain local copies for offline use.

---

### Post by michael-piziak on 2013-12-29
Mine also says "IMAP Mail Server"
and my server is: imap.suddenlink.net

I suppose I could change it to save sent emails to "local folder"

But where does it go, I tried that, and when clicking sent the email isn't there (as I do want to keep a copy of what's sent)

I just did another test, sent a 2.2 meg file, and it is taking what seem forever, like 5 minutes or longer to save copy to sent folder.

I wander if everyone's does this.  Should I attempt to uninstall and reinstall thunder bird mail?

---

### Post by michael-piziak on 2013-12-29
I see now, the local folder is the 2nd set down under "local folder".  I can choose to have it just put there

---

### Post by michael-piziak on 2013-12-30
Today, I deleted the ".thunderbird" hidden file, removed Thunderbird & reinstalled & chose Pop3 this time (instead of iMap).  Now everything works perfectly.

Marking this thread as solved.

Thanks so much for your help.

---

### Post by SeijiSensei on 2013-12-30
Just remember that, with POP, you will only be able to read your mail from the computer using Thunderbird.  In most cases, once you download your messages, they will be removed from the server. IMAP is preferable if you roam and need access to the mailbox from multiple clients, say your computer and a web-based interface.

It is possible to configure POP to leave your mail on the server when read, but not all providers support that feature.  Even in that case, only the inbox will be available rather than a complete folder structure.

---

### Post by michael-piziak on 2013-12-30
Got it.  When I roam, I just use my ISP's web based email.
Thanks.

---


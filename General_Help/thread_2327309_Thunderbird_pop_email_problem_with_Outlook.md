---
title: "Thunderbird pop email problem with Outlook"
date: 2016-06-09
forum: General Help
---

### Post by spideryada on 2016-06-09
I've solved this problem but want to share the fix. 

Thunderbird stopped receiving my MSN (Outlook) emails complaining that the user name or password was incorrect.

There was a change in the Outlook web page and they turned off the ability to use their pop server.

First sign in to Outlook.com -> Settings -> Connected accounts -> POP and IMAP
Click Yes - Let apps use POP
Click Let apps delete messages

Go to Thunderbird -> Outllook account -> Settings -> Server settings -> Server name
Paste pop-mail.outlook.com
Go to Outgoing Server (SMTP) -> Microsoft Live -> edit -> Server name
Paste smtp-mail.outlook.com

---

### Post by X-RED_Tech on 2016-06-09
Why would you want to use POP instead of IMAP?

---

### Post by spideryada on 2016-06-09
> **X-RED_Tech said:**
> Why would you want to use POP instead of IMAP?

Thunderbird asks for the POP server name but does not have the choice to change that to IMAP. Probably got set when the wizard set up the account years ago.

I just set up a new Outlook account in Thunderbird and it chose IMAP.

---


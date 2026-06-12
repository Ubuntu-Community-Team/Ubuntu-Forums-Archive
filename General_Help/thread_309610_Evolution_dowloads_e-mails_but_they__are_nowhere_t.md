---
title: "Evolution dowloads e-mails but they  are nowhere to be found"
date: 2006-11-29
forum: General Help
---

### Post by Aleksandersen on 2006-11-29
Hi,

I have a strange problem. Sometimes I see Evolution fetching e-mails... It is downloading say five or four messages. But when the download possess ends; no message shows up in the inbox, trash nor junk folder.

Where do they go?

It just happens to some messages and it happens from all e-mail accounts.

---

### Post by dcstar on 2006-11-30
> **Aleksandersen said:**
> Hi,

I have a strange problem. Sometimes I see Evolution fetching e-mails... It is downloading say five or four messages. But when the download possess ends; no message shows up in the inbox, trash nor junk folder.

Where do they go?

It just happens to some messages and it happens from all e-mail accounts.

IMAP or POP?

---

### Post by Aleksandersen on 2006-11-30
All accounts are POP/SMTP(+SSL).

---

### Post by schongal on 2008-04-06
> **Aleksandersen said:**
> All accounts are POP/SMTP(+SSL).

I would like to bump up this ancient thread, because i have been having the same exact problem for quite a while now.  I searched thru the ubunut forums but have not yet found a suitable answer.  And, I see the original question posed above was never answered in this thread, perhaps a knowledgeable person could please offer some help?:)

I have noticed this problem happens to me when I download Gmail (using POP) and the emails have attachments.  while evolution is taking the time to download the attachment, sometimes I get excited and click somewhere else on the evolution window which unfortunately causes the "send/receive mail" box to disappear.  Gmail and Evolution both think that the message has been downloaded to my computer.  and in fact, in ~.evolution/mail/pop/account_name, the text file containing the email body is present. BUT it does not show up in my evolution window.  and if I click "send/receive" again, the mail is not downloaded again.  Any ideas so far?

So in an effort to figure this out more, I am also wondering:  When I click "send/receive," does one of the following situations happen?  Can anyone enlighten me as to how exactly POP works, on a nuts & bolts level?
A) does evolution ask Gmail "Are there any messages I haven't seen yet?" and Gmail makes the decision to send or not send messages? or...
B) does evolution say "Send me mail," to which Gmail replies, "Here are the messages available," and Evolution responds, "I'll take emails 002, 003, and 004.  I already have 001."

if its B, maybe I can slap evolution upside the head and make it re-download email 001, which it thinks i have, but it is retarded and wont display it.

If its A, maybe I can somehow go into Gmail and flag that message to be sent again?

Any ideas?

Thanks!
ms

---

### Post by tvor on 2008-07-06
I would be also very interested to answer to this great question!

---


---
title: "How To Tell If Thunderbird Is Responding To 'Get Mail'?"
date: 2014-04-16
forum: General Help
---

### Post by buzzingrobot on 2014-04-16
I need a way to see if Thunderbird is actually checking for new mail when I click its "Get Mail" button.

It polls for new mail every 10 minutes from an IMAP server.  No problem there.

But, when I click "Get Mail" I do not see the expected crawl of text along the bottom of Thunderbird's window announcing no mail, or some number of new messages.

In fact, there's no visible response at all. I've tried sending mail to myself and then clicking away, but the results are pretty inconclusive.

Is there a specifc process associated with this that I could watch for?

(Thunderbird 24.4.0 on 14.04 Unity)

---

### Post by SeijiSensei on 2014-04-16
Thunderbird will not report much about mailboxes that haven't changed since they were last polled.  If there are new messages in a mailbox, or if the client hasn't checked with the server for a while, you'll see an entry in the bottom status bar reporting on the number of messages being downloaded from the server.  Since I have dozens of mail folders, I almost always see TBird downloading something when I first start it up.  After that, the only real indication is that folders with new messages are displayed in bold text.

---

### Post by buzzingrobot on 2014-04-16
Thanks. I'll stop fretting.  I just switched mail providers and thought something might have been a bit off.

[On second thought: if I close and open Thunderbird, I do see a series of messages displayed along the bottom as it checks for mail, whether or not there's any new mail on the server.  I don't see those messages if I click 'Get Mail'. (I could swear they've been there before.)  A quick Google turned up several reports of similar behavior with 24.4.0.]

---

### Post by ddraper2 on 2014-04-16
Use the Tools->Activity Manager menu entry. This will display a list of all the activity that Thunderbird has performed. This should tell you what you are looking for.

---

### Post by buzzingrobot on 2014-04-16
Actvity Manager here does show successful downloads of messages.  If I clear it, then click "Get Mail", it stays cleared and empty. There's nothing to indicate the server was polled for new mail, just as there is no indication given in the main window.  

Maybe I'm imagining it, but doesn't Thunderbird typically post a "no new mail..." message when that's the case?

---

### Post by SeijiSensei on 2014-04-17
I don't recall seeing one.  All I observe is that a mailbox with unread messages appears in bold text with the number of new messages in parentheses at the end.

---

### Post by dragonfly41 on 2014-04-17
pop3browser utility can run terminal commands to quickly scan your server for any new mail before launching Thunderbird.

---

### Post by col48 on 2014-04-17
What I see when I click Get Mail when there is nothing incoming is a very rapid blur of messages in the bottom bar and the final one (There are no new messages for ...) stays there until replaced by something else.

Activity Manager tells me when there were no messages to download but does not tell me it tried because I clicked Get Mail.

I'm not using IMAP but POP3, have multiple email accounts being checked, and do not automatically download mail.
This is Thunderbird 24.4.0 on Precise 64-bit.

Hope this helps a bit.

---

### Post by buzzingrobot on 2014-04-17
> **col48 said:**
> What I see when I click Get Mail when there is nothing incoming is a very rapid blur of messages in the bottom bar and the final one (There are no new messages for ...) stays there until replaced by something else.



Thanks.  I don't see those messages when I click 'Get Mail', but I do see them when I open Thunderbird and it checks for new mail, as well as when it automatically checks for new mail and there isn't any. 

I very recently switched to a new mail provider, so I'm going to guess this is down to a combination of its IMAP configuration and 24.4.0.  I've seen several complaints from Windows users that 24.4.0 is "not working" when 'Get Mail' is used.  I don't think that's the case, but, in this instance, it is definitely not providing any indication that it *is* working.

---

### Post by ddraper2 on 2014-04-17
I am running 24.4.0 under Ubuntu 13.10 64-bit. Using IMAP against my own domain (mail server hosted by 1&1) and Yahoo & GMail. No problems.

If I select get mail I will see the messages flash by in the lower left as it cycles through all the email accounts.

---

### Post by buzzingrobot on 2014-04-17
Well, I let netstat take a look and it shows a blip of bytes going out to the server when I click 'Get Mail'.  So, I guess they're talking. Still, it's disconcerting not to get a visual confirmation.

Marking this solved, sort of...

---


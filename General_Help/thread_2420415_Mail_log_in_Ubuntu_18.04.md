---
title: "Mail log in Ubuntu 18.04"
date: 2019-06-05
forum: General Help
---

### Post by gawardnz on 2019-06-05
Hi,

I have 100's of spam emails flooding my inbox (bounced by mail servers as being undeliverable) every other day. I have read online that it may not necessarily be emails sent by my computer, however I am curious as to how/why they are reflected as being sourced from me when the sender is somebody else altogether different. Now, with that said, I would like to confirm whether or not the emails are in fact coming from my computer (by way of some malware that has found itself onto my computer somehow). I have my doubts, but would like to confirm this. I have read that Linux/Ubuntu stores a mail log for all emails sent under /var/log/maillog or /var/log/mail.log however I do not see these log files in my computer. Where does Ubuntu (version 18.xx) store logfiles regarding any/all sent emails?

Thanks for the help.

---

### Post by kpatz on 2019-06-05
You would only see a mail log if you have a MTA such as postfix, sendmail or exim installed on your system, and the outgoing mail is being relayed through it.  If you have a spambot sending the messages, it probably won't leave many traces in normal logs.

If you examine the bounces, can you see the headers of the original emails that were bounced back?  The Received: headers should show the original sending IPs.

Sometimes spammers will use someone's email address as the "sending" address, so the bounces go back to the innocent user.

It may not be that specific (Ubuntu) system that is sending them either.  Do you have any other computers connected to the internet that have your email address set up on them in a client?  Especially Windows systems?  Also, if your email is web/cloud based (something like gmail, Yahoo, Outlook.com etc) they could have gotten your password and are sending the mails from there.  Check your sent folder on the email account if this is the case.  Also check your account activity to see if it's being logged in to from a location you don't recognize, and change your password on the account (make it strong!!!)

---

### Post by SeijiSensei on 2019-06-05
You need to expose the entire set of headers to know what's going on.  The "Return-Path" header shows the actual origination of the message. The "From:" header in the message can be forged, but the "envelope sender" in the Return-Path cannot.  You should spend some time reading all the headers of a representative message to see where it originated and how it got to you.

---


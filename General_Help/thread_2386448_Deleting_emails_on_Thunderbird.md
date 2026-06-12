---
title: "Deleting emails on Thunderbird"
date: 2018-03-06
forum: General Help
---

### Post by freesitebuilder on 2018-03-06
I'm using 16.04 LTS 64-bit, Thunderbird 52.6

I manage several email accounts for my voluntary work, plus two personal accounts. I've used Thunderbird since it became default for Ubuntu, and for many years when I was running windows ten years ago. I use the page preview layout - email list at top, preview pane showing highlighted email at the bottom. This bottom pane has delete and archive buttons for the current email being viewed.

I recently created a new account for an additional email address, and the delete button does nothing. I spent some time comparing settings with my other accounts, couldn't find anything, and gave up - it doesn't get much email.

Then I got the same problem on my main personal account, which has worked perfectly for years. To delete, I have to right-click the email in the top pane list, and choose "move to deleted again". All my other accounts are still working OK.

Anyone else have this issue? I can't find anything on Mozilla forums, and I can't see it being an Ubuntu problem or it would be right across all my email accounts.

TIA

---

### Post by ajgreeny on 2018-03-06
Are these email accounts pop3 or IMAP?

The settings of your email provider's server will affect what happens at that end so do you know if all messages are deleted from their server after you have read them or do they remain on the server but archived and marked as read so that they are not downloaded again next time?

I think your problem must be more related to the server, not your T'Bird installation as I have also been using T'Bird for many years and mine is working exactly as expected with delete button for emails working in both pop3 and IMAP accounts.

---

### Post by col48 on 2018-03-06
For what it's worth, I'm sure ajgreeny is right.  It's server behaviour which is the root of the issue.

Like the OP, I use Tb 52.6 in Xenial, but also (earlier version of Tb) occasionally in Precise.  Using IMAP exclusively.  The behaviour is the same for each.

As of about a year ago Tb was sometimes (always after Oct last year) unable to find the server for the two Outlook-based accounts I use. Since gmail has continued to be OK, I now forward all email on the Outlook accounts to a dedicated gmail account, so I have experience of both.

None of these accounts remember the deletion of emails after the end of the session (including sessions when I login via the relevant website), although I think they do have a limited retention period (6 months?  a year?).  I keep emails off-line so would be very content for the cloud servers not to do so...

I believe IMAP is intended to enable folk to access emails across a number of devices, so I can understand - up to a point - that it should be more difficult to erase them, but surely not to appear to delete when they don't actually do so?  Legislation/government policy is a factor, too, of course.

---

### Post by freesitebuilder on 2018-03-06
These are all POP3 -  have three on one server, two work fine, one doesn't. My other problem account is one of my personal accounts, the only account I have on another server.

I leave all mails on server for 14 days so I can access them by webmail at work when necessary. they are marked as read and only download once.

---


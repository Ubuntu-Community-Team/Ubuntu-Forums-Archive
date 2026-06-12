---
title: "gmail - deleting emails"
date: 2017-05-15
forum: General Help
---

### Post by col48 on 2017-05-15
An annoyance, not a show-stopper.

I prefer to keep all my gmail emails on my desktop, so regularly download any new ones and delete them from the cloud.
Except they do not stay deleted (even with Shift+Delete).
They appear to be deleted but next session or after a day or few they reappear.
Sometimes they reappear in Inbox, sometimes in Deleted, sometimes only(?) in AllMail.

Why don't they just disappear immediately?

They do eventually disappear, but I don't know what brings this about.

---

### Post by ajgreeny on 2017-05-15
How do you access the email account, webmail in a browser or using an application, eg thunderbird?
Is this using pop3 or imap?

What settings do you have for the gmail account, not at your client, but at the gmail server.
To make changes to any settings go to gmail in a webbrowser, sign in and then click on the cog icon top right of the page ->Settings ->"Forwarding and POP/IMAP" tab and see if there is anything there that looks as if could be the problem.

Having never seen this happen I can not help with any more suggestions.

---

### Post by Bucky Ball on 2017-05-15
Along similar lines to aj: have you tried deleting them from Gmail directly? Like logging in and deleting them? If you have some feed coming directly from Gmail to your desktop set up, every time you open the computer and go online it will refresh directly from the Gmail server and, sure enough, there will be your emails. This is my hypothesis.

Delete them in Gmail directly and see if you get the same issue next time you start the machine.

---

### Post by col48 on 2017-05-15
@ajgreeny

Thanks - I think I may have found what's going on thanks to your suggestion.

I am using Thunderbird, IMAP and up to now just the defaults at the server end.  I'd just never investigated them!

One section under Forwarding under POP/IMAP reads (where I have marked the options set with #):
```
IMAP Access:
(access Gmail from other clients using IMAP)
Learn more	
Status: IMAP is enabled
#	Enable IMAP
	Disable IMAP

When I mark a message in IMAP as deleted:
	Auto-Expunge on - Immediately update the server. (default)
#	Auto-Expunge off - Wait for the client to update the server.

When a message is marked as deleted and expunged from the last visible IMAP folder:
	Archive the message (default)
#	Move the message to the Trash
	Immediately delete the message forever



```
I suspect I want to set Auto-Expunge to 'on' (and will do so now!).  At what point would the client update the server - is it when I send an email, not very often on this account?

@Bucky Ball
I don't open Thunderbird on login and don't have gmail automatically download - indeed I don't even look at gmail every time I open Thunderbird as it is not my main account.  Both are manual actions, and I get so little junk/spam that this is not a big chore.

I think you are right in saying that deleting in the web browser would be likely to kill the emails, but I would not choose to go via the web browser routinely.  Managing emails is what I have Thunderbird for!

Thanks for your response.

---


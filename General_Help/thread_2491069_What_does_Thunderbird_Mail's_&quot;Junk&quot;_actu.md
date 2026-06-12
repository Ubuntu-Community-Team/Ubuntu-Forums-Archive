---
title: "What does Thunderbird Mail's &quot;Junk&quot; actually do?"
date: 2023-09-25
forum: General Help
---

### Post by johnnybegood2222 on 2023-09-25
What does Thunderbird Mail's "Junk" actually do?

I keep clicking that incoming emails are junk; however, I've noticed I still get emails from the same junk sender.  Isn't "junk" suppose to make it to where I don't see emails coming in from a sender that I've already clicked on as junk?

---

### Post by TheFu on 2023-09-25
No. It doesn't work that way, since the "from" address can be forged, trivially.  Would you like a message from God or Dog?  That's easy for anyone running an email server to send.  In the old days, it was trivial to send a message from [email]god@heaven.org[/email] (non-profit, clearly).

a) don't remove the messages in the junk folder
b) Use filters based on the x-headers
c) look at what spam filtering your email server provider give you.  Mine provides the ability to perform server-side filtering so thunderbird really isn't involved in any filters for me.  

The online Thunderbird help has this: [https://support.mozilla.org/en-US/kb/organize-your-messages-using-filters](https://support.mozilla.org/en-US/kb/organize-your-messages-using-filters)
and [https://support.mozilla.org/en-US/questions/1362132](https://support.mozilla.org/en-US/questions/1362132)
Be certain that _adaptive junk mail controls_ for the account are enabled.

---

### Post by ian-weisser on 2023-09-25
> **TheFu said:**
> Be certain that _adaptive junk mail controls_ for the account are enabled.

Couldn't say it better, so quoted. Yes, that's really the key to using the Junk tool effectively.

Note that Junk's learning process includes false positives. So review Junk every few days and un-Junk emails that you actually want before deleting the contents of the folder.

---

### Post by johnnybegood2222 on 2023-10-01
I need a way to quickly click a button, like the junk button, to filter out emails.  I get SO MUCH spam email.

---

### Post by TheFu on 2023-10-01
> **johnnybegood2222 said:**
> I need a way to quickly click a button, like the junk button, to filter out emails.  I get SO MUCH spam email.

I think you are trying to solve this the wrong way.  Let the computer handle it.  "J" when a message is selected will mark it as "Junk" and re-file it to the Junk folder. "Shift-J" will remove a selected message from the Junk folder, back to the inbox.  There's a "Junk" button when a message is selected.  
I run Thunderbird in a 3 panel mode. that's the View --> Layout ---> Classic View mode. Folder list on the left, Message list top-right and a selected message bottom right.  There's a Junk button between the two right-hand panels.

Set your "Junk" folder to be clean up every 60 days, automatically. There's a setting in Thunderbird for that.  "Automatically delete Junk Mail older than  XX days." That should provide enough training.

In the settings for each different email account, there's "Junk Settings". There's a setting to tell thunderbird which server-added-headers to trust. Take advantage of that. My mail server has spamassassin which sets an estimated X-SPAM-SCORE level.  This is typically -10 through +12.    Anything less than 0 would be non-spam almost 100%.  Sometimes I'm overly aggressive so I don't need to deal with spam manually hardly ever. Sometimes, that means non-spam gets marked as spam.  For example, there are thousands of saved messages in my mail server.  I've been running the same software (upgraded from time to time) since 2008. That means all those messages have the X-SPAM-SCORE value in the message header.  A message from these forums was marked as spam with a 7.023 spam score.  I could setup a specific filter in thunderbird (or on the server) to automatically allow all email through from that address.

---

### Post by johnnybegood2222 on 2023-10-07
[U]adaptive junk mail controls


[/U]Can someone tell me what menu to find this to turn it on

Also to "TheFu" I am doing what you said also...

---

### Post by TheFu on 2023-10-07
> **johnnybegood2222 said:**
> [Can someone tell me what menu to find this to turn it on

Also to "TheFu" I am doing what you said also...

Right-click on the mail server in the server+folder panel --> Settings ---> Junk Settings
Each email server and email account has this. If you use multiple accounts, check them all.

---

### Post by jahangir121 on 2023-12-05
Nice

---

